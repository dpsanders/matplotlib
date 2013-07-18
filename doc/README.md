`matplotlib` documentation tree 
========================

This is the top-level directory of the ``matplotlib``
documentation tree.  

The `matplotlib` documentation is written using [Sphinx](http://sphinx-doc.org/), a
Python documentation system built on top of the lightweight markup language [ReStructuredText](http://docutils.sourceforge.net/rst.html) (ReST).

## Contents

This directory contains the following subdirectories:


* [users](./users) -- the user documentation, including plotting tutorials and configuration tips

* [devel](./devel) -- documentation for `matplotlib` developers

* [faq](./faq) -- frequently asked questions

* [api](./api) -- placeholders to automatically generate the API documentation

* [mpl_toolkits](./mpl_toolkits) -- documentation of toolkits that ship with `matplotlib`

* [sphinxext](./sphinxext) -- `sphinx` extensions for the `matplotlib` docs

* [mpl_examples](./mpl_examples) - a symbolic link to the `matplotlib` examples (found in the directory above), so that examples may be referenced from within the documentation

* [_static](./_static) -- used by the `sphinx` build system

* [_templates](./_templates) -- used by the `sphinx` build system
  

and the following files:


* [make.py](./make.py) -- the main script used to build the HTML and  PDF documentation

* [index.rst](./index.rst) -- the top-level include document for `matplotlib` documentation

* [conf.py](conf.py) -- the `sphinx` configuration


## Building the documentation

### Building the `matplotlib` package

Since `sphinx` uses the installed version of `matplotlib` to build
the documentation, the whole package must be installed *before* the docs
can be generated. 

Furthermore, even if `matplotlib` is already installed on your system, it is *not* possible to build the documentation without first building the 
`matplotlib` package, since the file [../lib/matplotlib/mpl-data/matplotlibrc](../lib/matplotlib/mpl-data/matplotlibrc), which is required during the process, is itself created
during the `matplotlib` build process. 

To build the `matplotlib` package, run the command




	python setup.py build

from the root of the source tree.


### Building the documentation

To build the HTML documentation, `sphinx` (version >= 1.0)
is required. 

First the example gallery must be built, by running the command

	python make.py html

from within the current directory (`doc`). The gallery is then located at [build/html/gallery.html](build/html/gallery.html).

Now the documentation build is completed by repeating the same command:

	python make.py html 

The entry point for the HTML documentation is now available at [build/html/index.html](./build/html/index.html).


Since the documentation takes a long time to build, it is possible to
 build a reduced version, which does not include
high-resolution PNGs and PDFs. To do so, run the command

	python make.py --small html

To build the PDF documentation, replace `html` by `pdf` in the above commands.
