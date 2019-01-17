=====================
 run-clang-format.py
=====================
----------------------------------------------
 Lint files and directories with clang-format
----------------------------------------------

.. contents::
   :local:

Introduction
============

A wrapper script around clang-format, suitable for linting multiple files
and to use for continuous integration.

This is an alternative API for the clang-format command line.
It runs over multiple files and directories in parallel.
A diff output is produced and a sensible exit code is returned.

.. image:: screenshot.png


How to use?
===========

Copy `run-clang-format.py <run-clang-format.py>`_ in your project,
then run it recursively on directories, or specific files::

  ./run-clang-format.py -r src include foo.cpp

It's possible to exclude paths from the recursive search::

  ./run-clang-format.py -r \
      --exclude src/third_party \
      --exclude '*_test.cpp' \
      src include foo.cpp

Docker
======
  docker run -v "$(pwd)":/files [imagename] [arguments]

FAQ
===

Can I check only changed files?
-------------------------------

No, and this is what this repository was initially about.
However, once working around a few shortcommings of ``git clang-format``,
I opted to try an alternative strategy
which expects the whole project to be correctly formatted.

It would make sense to support this feature as well,
so that the coding style does not need to be enforced but merely suggested.
