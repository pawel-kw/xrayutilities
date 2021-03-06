xrayutilities
=============

[![Build
Status](https://travis-ci.org/dkriegner/xrayutilities.svg?branch=master)](https://travis-ci.org/dkriegner/xrayutilities)

xrayutilities is a collection of scripts used to analyze x-ray diffraction
data.  It consists of a Python package and several routines coded in C. It is
especially useful for the reciprocal space conversion of diffraction data
taken with linear and area detectors.


Copyright (C) 2009-2016 Dominik Kriegner <dominik.kriegner@gmail.com>

Copyright (C) 2009-2013 Eugen Wintersberger <eugen.wintersberger@desy.de>



Contents
--------

* *examples*:           directory with example scripts and configurations
* *xrayutilities*:      directory with the sources for the Python package
* *tests*:              directory with the unittest scripts
* *setup.py*:           distutils install script used for the package installation
* *xrayutilities.pdf*:  pdf-file with documentation of the package

Installation
============
Installing xrayutilities is an easy process done by executing

    python setup.py install

or

    python setup.py install --prefix=<install_path>

in the source folder of xrayutilities on the command line/terminal.  The first
command installs in the systems default directories, whereas in the second
command you can manually specify the installation path.

By default the setup.py script tries to use OpenMP. If you do not want to use
OpenMP or do not have it available use the *--without-openmp* option for the
installation:

    python setup.py --without-openmp install --prefix=<install_path>

Requirements
------------
The following requirements are needed for installing and using *xrayutilities*:

- Python (version 2.7 or >= 3.2)
- C-compiler (preferential with OpenMP support)
- h5py
- scipy (version >= 0.11.0)
- numpy (version >= 1.8)
- lmfit (optionally)
- matplotlib (optionally)
- unittest2 (optionally - only if you want to run the tests)
- numpydoc (optionally - only when you want to build the documentation)

refer to your operating system documentation to find out how to install
those packages. On Microsoft Windows refer to the Documentation for the
easiest way of the installation (Python(x,y) or WinPython).

Python-2.7 and Python-3.X compatibility
=======================================

The current developement focuses on Python-3.X and we ask all users to update
to Python-3 if possible, however, xrayutilies can be used with Python-2.7 as well.
Care was taken to make this possible from the same code-base.

The Python package configuration
================================

The following steps should only be necessary for user local installation to
ensure the Python module is found by the Python interpreter:
In this case the module is installed under
*<prefix>/lib[64]/python?.?/site-packages* on Unix systems and
*<prefix>/Lib/site-packages* on Windows systems.

If you have installed the Python package in a directory unknown to your local
Python distribution, you have to tell Python where to look for the Package.
There are several ways how to do this:

- add the directory where the package is installed to your
  *PYTHONPATH* environment variable.

- add the path to sys.path in the *.pythonrc* file placed in your home
  directory

      import sys
      sys.path.append("path to the xrayutilities package")

- simply apply the previous method in every script where you want to
  use the xrayutilities package before importing the package

      import sys
      sys.path.append("path to the xrayutilities package")
      import xrayutilities

Obtaining the source code
=========================

The sources are hosted on sourceforge in git repository.
Use

    git clone git://git.code.sf.net/p/xrayutilities/code xrayutilities

to clone the git repository. If you would like to have commit rights
contact one of the administrators.

Update
======

if you already installed xrayutilities you can update it by navigating into
its source folder and obtain the new sources by ::

    git pull

or download the new tarball from sourceforge
(http://sf.net/projects/xrayutilities) if any code changed during the update you
need to reinstall the Python package.  To determine the path in which
xrayutilities where installed previously use

    python -c "import xrayutilities as xu; print xu.__file__"
      /usr/local/lib64/python2.7/site-packages/xrayutilities/__init__.pyc

if the output is e.g.: */usr/local/lib64/python2.7/site-packages/xrayutilities/__init__.py*
you previously installed xrayutilities in */usr/local*, which should be used
again as install path. Use ::

    python setup.py install --prefix=<path to install directory>

to install the updated package.


Documentation
=============

Documention for xrayutilities is found in the *xrayutilities.pdf* file or on the
webpage http://xrayutilities.sourceforge.net

The API-documentation can also be browsed by

    pydoc -p PORT

in any web-browser, after the installation is finished.

To build the PDF documentation from the docu-sources use:

    python setup.py build build_doc -b pdf

You will need sphinx, numpydoc and rst2pdf.

Or generate a texinfo file using

    python setup.py build_doc -b texinfo
    cd build/sphinx/texinfo; make


Packaging
=========

create a tarball for redistribution of xrayutilities without the use of git

    python setup.py sdist

creates a tarball in the directory dist, which contains everything needed for
the installation of xrayutilities


