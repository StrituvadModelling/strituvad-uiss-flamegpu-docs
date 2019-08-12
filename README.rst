STriTuVaD UISS FLAME GPU Documentation
========================================

.. image:: https://readthedocs.org/projects/flame-gpu-uiss/badge/?version=latest
   :target: https://flame-gpu-uiss.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status

.. image:: https://travis-ci.org/RSE-Sheffield/strituvad-uiss-flamegpu-docs.svg?branch=master
    :target: https://travis-ci.org/RSE-Sheffield/strituvad-uiss-flamegpu-docs

This is the public facing documentation for the FLAME GPU 1.5 implementation of the UISS 6 simulator, as part of the `STriTuVaD <https://www.strituvad.eu/>`_ H2020 project.

Funding 
-------

This project has received funding from the European Research Council (ERC) under the European Union's Horizon 2020 research and innovation programme (grant agreement n. 777123).

https://cordis.europa.eu/project/rcn/212940/factsheet/en

How to Contribute
-----------------
To contribute to this documentation, fork this repository on GitHub and create a local clone of your fork on your local machine, see `Fork a Repo <https://help.github.com/articles/fork-a-repo/>`_ for the GitHub documentation on this process.

Create changes in a feature-branch and push to your fork. Please ensure that the documentation can still be built after your changes have been made (see `Building the documentation`).

Once you have made your changes and updated your Fork on GitHub you will need to `Open a Pull Request <https://help.github.com/articles/using-pull-requests/>`_. All changes to the repository should be made through Pull Requests, including those made by the people with direct push access.


Building the documentation on Linux
-----------------------------------

#. Ensure Python 3 (ideally Python >= 3.6) is installed.
#. Create a `virtual environment <https://docs.python.org/3/tutorial/venv.html>`_ to install sphinx into: ::

    mkdir -m 700 ~/.venvs
    python3 -m venv ~/.venvs/strituvad-uiss-flamegpu-docs
    source ~/.venvs/strituvad-uiss-flamegpu-docs/bin/activate

#. Install the Python packages needed to build the HTML documentation: ::

     pip install -r requirements.txt

#. Build the documentation: ::

     cd docs/
     make html

#. Open the documentation: ::
     
     xdg-open _build/html/index.html

Continuous build and serve
##########################

The package `sphinx-autobuild <https://github.com/GaretJax/sphinx-autobuild>`_ provides a watcher that automatically rebuilds the site as files are modified. To use it, install (in addition to the Sphinx packages) with the following: ::

    pip3 install sphinx-autobuild

To start the autobuild process, run: ::

    make livehtml

The application also serves up the site at port ``8000`` by default at http://localhost:8000.
