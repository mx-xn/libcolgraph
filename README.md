## libcolgraph
[![pipeline status](https://aalok-sathe.gitlab.io/libcolgraph/build.svg?v=1749532520)](https://gitlab.com/aalok-sathe/libcolgraph)

a coloring graphs library written in C++ for speedy computation and wrapped in
Python for ease of development and extension!

### what
this library provides support to construct graphs, their coloring graphs, and
biconnected component metagraphs.
a coloring graph is a graph representing all the valid colorings of a graph.
each vertex of a coloring graph represents a coloring of the base graph.
two colorings are considered adjacent if they differ in only one vertex's color.

in this project, we represent a coloring as an integer, which, when converted to
base k (for a k-coloring), is a number of length |V| and represents the vertex-wise
colors [0,k) for each vertex.

the library is under development, being written using Python and C/C++.
the web application uses the library to provide useful GUI for quick drawing and
graph construction.
in the future, we plan to develop a supplemental subsection of the library containing
useful graph algorithms and ability to run simulations to test structural graph theoretic
conjectures about graph coloring and coloring graphs.
for documentation, feel free to take a look inside `libcolgraph/` and read the docstrings.
for questions, reach out.

### screenshot of the web GUI

  [Clockwise]
  A 7 vertex BaseGraph that is a hexagon with a central vertex and a missing 'spoke'
  leads to a quite complex ColoringGraph with k=4 colors. You can see the formation of
  polyps at the edges. The structure of the resultant ColoringGraph is shown in the
  Meta ColoringGraph produced by a run of modified Tarjan's algorithm for biconnected
  components. The central 'mothership' can be seen, adjacent to which there are cut
  vertices, and finally the stray singular coloring vertices at the tips of polyps.

  <img src="https://i.imgur.com/TusisoA.png" />

  for a static demo, go to the project's [gitlab pages](https://aalok-sathe.gitlab.io/libcolgraph). 

### usage
- as a module

  plot a BaseGraph, its ColoringGraph, and the Meta
  ColoringGraph generated by Tarjans. you would need to
  have a graph formatted in an adjacency matrix file.
  opens plots in new browser windows.

  launch web GUI:
  ```
    libcolgraph.web [-h] [-i INPUT_FILE] [-n] [-s] [-k COLORS] [-v] [-p PORT]
                       [-w] [-r] [-d] [-t]

    optional arguments:
      -h, --help            show this help message and exit
      -i INPUT_FILE, --input-file INPUT_FILE
                            read in BaseGraph from adjacency matrix file
      -n, --new             open a blank canvas?
      -s, --select_file     open file choosing gui dialogue?
      -k COLORS, --colors COLORS
                            number of colors to use to create ColoringGraph
      -v, --verbosity       set output verbosity
      -p PORT, --port PORT  port to launch GUI on
      -w, --webbrowser      open app in default web browser window?
      -r, --render_on_launch
                            render to-generate componenets on initial launch?
      -d, --debug           launch Flask app in debug mode?
      -t, --threaded        allow multiple threads?
  ```

- as a library

    ```python
    import libcolgraph

    bg = libcolgraph.BaseGraph()
    bg.load_txt('./in/hexmod.in')

    cg = bg.build_coloring_graph(4)

    print('bg {} led to a cg {}'.format(bg, cg))

    for v in cg.get_vertices():
        print(v)
        
    ```


### installation

- for installation from source
    refer to [detailed install instructions](INSTALL.md)


- [pypi](https://pypi.org/project/libcolgraph/)

    ```bash
    python3 -m pip install libcolgraph [--upgrade]
    ```

    things to note:
    - currently a binary wheel is available only for [`manylinux`](https://www.python.org/dev/peps/pep-0513/)
      distributions e.g. centOS, Debian family, RedHat family, etc.
    - if your distribution is not `manylinux`-supported, then pip
      will need to compile locally using `swig` and `setuptools`.
      in that case, make sure you have `setuptools` and
      [swig](http://www.swig.org/download.html) installed, as they
      will be needed for compilation.
    - we periodically release wheels for MacOS as well. these
      might not be as frequently maintained, however, so your best
      bet would be to compile locally using `swig`.


### contribute

see [contributing guide](CONTRIBUTING.md)

### help

visit [full API documentation](https://aalok-sathe.gitlab.io/libcolgraph)


### who

Coloring Graphs lab, University of Richmond.
(C) 2017-2020




















