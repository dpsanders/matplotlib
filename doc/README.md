`matplotlib` documentation tree 
========================

This directory (`doc`) is the top-level directory of the ``matplotlib``
documentation tree.  

The `matplotlib` documentation is written using [Sphinx](http://sphinx-doc.org/), a
Python documentation system built on top of the lightweight markup language [ReStructuredText](http://docutils.sourceforge.net/rst.html) (ReST).

## Contents

This directory contains the following top-level documentation build files:


* [make.py](./make.py) -- main Python script to build the HTML and  PDF documentation

* [contents.rst](./index.rst) -- master document which pulls in all 
`matplotlib` documentation

* [conf.py](conf.py) -- configuration file for `sphinx`


The documentation proper is arranged into the following subdirectories:


* [users](./users) -- user documentation, including plotting tutorials and configuration tips

* [devel](./devel) -- documentation for `matplotlib` developers

* [faq](./faq) -- frequently-asked questions

* [glossary](./glossary) -- glossary of useful terms

* [pyplots](./pyplots) -- examples for the screenshots page

* [api](./api) -- placeholders to automatically generate API documentation

* [mpl_toolkits](./mpl_toolkits) -- documentation for toolkits shipped with `matplotlib`

* [sphinxext](./sphinxext) -- `sphinx` extensions for `matplotlib` documentation

* [mpl_examples](./mpl_examples) - symbolic link to top-level [examples](../examples) directory, so that examples may be referenced from within documentation

* [_static](./_static) -- used by the `sphinx` build system

* [_templates](./_templates) -- used by the `sphinx` build system
  


## Building the documentation

### Building the `matplotlib` package

Since `sphinx` uses the installed version of `matplotlib` to build
the documentation, the whole package must be installed *before* the docs
can be generated. 

Furthermore, even if `matplotlib` is already installed on your system, it is *not* possible to build the documentation without first building the 
`matplotlib` package, since the needed file [../lib/matplotlib/mpl-data/matplotlibrc](../lib/matplotlib/mpl-data/matplotlibrc) is itself created
during the `matplotlib` build process. 

To build the `matplotlib` package, run the command

	python setup.py build

from the [root](..) of the source tree.


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

To build the PDF documentation, replace `html` by `latex` in the above commands.

To clean the documentation, i.e. to remove the generated files, run

	python make.py clean
