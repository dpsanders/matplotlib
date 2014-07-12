matplotlib documentation tree
=================================

The current directory (doc) is the top level of the matplotlib
documentation tree.

The matplotlib documentation is written using Sphinx, a Python documentation
system built on top of the lightweight markup language reStructuredText.

Contents
--------

This directory contains the following top-level documentation build
files:

- make.py -- main Python script to build the HTML and PDF documentation

- contents.rst -- master document containing the specification for the
                   global documentation structure

- conf.py -- configuration file for Sphinx


The documentation is arranged into the following subdirectories:

- users -- user documentation, including plotting tutorials and configuration tips

- devel -- documentation for matplotlib developers

- faq -- frequently-asked questions

- glossary -- glossary of useful terms

- pyplots -- examples for the screenshots page

- api -- placeholders to automatically generate API documentation

- mpl_toolkits -- documentation for toolkits shipped with matplotlib

- sphinxext -- ``sphinx`` extensions for ``matplotlib`` documentation

-  mpl_examples -- symbolic link to top-level examples directory, so that
                   examples may be referenced from within documentation

-  _static -- used by the Sphinx build system

-  _templates -- used by the Sphinx build system


Building the documentation
--------------------------

Sphinx uses the result of *building* the matplotlib package
itself in order to generate the documentation; so this build must be
performed *before* the documentation can be generated.

Furthermore, even if matplotlib is already installed on your system,
it is *not* possible to build the documentation without first building
the matplotlib package, since the needed file
../lib/matplotlib/mpl-data/matplotlibrc is itself created during the
matplotlib build process.

Building the matplotlib package
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Begin by building the matplotlib package, using the command

::

    python setup.py build

from the root <..> of the source tree.

Building the documentation
~~~~~~~~~~~~~~~~~~~~~~~~~~

To build the HTML documentation, Sphinx (version >= 1.0) is
required.

Example gallery
^^^^^^^^^^^^^^^

First, the example gallery is built, by running the command

::

    python make.py html

from within the current directory (doc). The gallery is built at
build/html/gallery.html.

Complete documentation
^^^^^^^^^^^^^^^^^^^^^^

Now the documentation build is completed by repeating the same command:

::

    python make.py html

The entry point for the HTML documentation is now available at
build/html/index.html.

Reduced process
^^^^^^^^^^^^^^^

Since the documentation takes a long time to build, it is possible to
build a reduced version, which does not include high-resolution PNGs and
PDFs. To do so, run the command

::

    python make.py --small html

PDF output
^^^^^^^^^^

To build the documentation in PDF format, replace ``html`` by ``latex`` in the
above commands.

Cleaning
^^^^^^^^

To clean the documentation, i.e. to remove the generated files, run

::

    python make.py clean
