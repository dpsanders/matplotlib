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


* `make.py` -- the main script used to build the HTML and  PDF documentation

* `index.rst` -- the top-level include document for `matplotlib` documentation

* `conf.py` -- the `sphinx` configuration


## Building the documentation


To build the HTML documentation, install `sphinx` (version 1.0 or greater
is required), then type 

	python make.py html

from within this directory (`doc`).  

Wait
for the initial run, which builds the example gallery, to be done,
then run the same command for a second time:

	python make.py html 

The entry point for the HTML documentation is now available in `./build/html/index.html`

Note that `sphinx` uses the installed version of the package to build
the documentation, so `matplotlib` must be installed *before* the docs
can be generated. 

Even if that is the case, one of the files needed
to do this, `../lib/matplotlib/mpl-data/matplotlibrc`, is created
in the `matplotlib` build process. This means that the
documentation *cannot* be generated immediately after checking out the
source code, even if `matplotlib` is installed on your system; rather, it is required to first build `matplotlib` by running

	python setup.py build

from the root of the source tree.

Since the documentation takes a long time to build, it is possible to
 build a reduced version, which does not include
high-resolution PNGs and PDFs. To do so, run the command

	python make.py --small html

To build the PDF documentation, replace `html` by `pdf` in the above commands.
