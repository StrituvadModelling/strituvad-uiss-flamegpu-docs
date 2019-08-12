.. _tools:

*****
Tools
*****

Several scripts / tools have been developed to simplify the use of the simulator, which can be found in the `RSE-Sheffield/strituvad-uiss-flamegpu repository <https://github.com/RSE-Sheffield/strituvad-uiss-flamegpu>`_. 

Further information and examples of all these scripts can be found in the `source repository <https://github.com/RSE-Sheffield/strituvad-uiss-flamegpu>`_.


Input File Conversion Script
============================

The FLAME GPU implementation of UISS 6 takes a FLAME GPU input file as an input parameter.
A Python script has been developed to convert a UISS input file in to an appropriately formatted FLAME GPU input file.

Usage is as follows: 

.. code-block:: bash

   # Convert 'datafile' to '0.xml'
   python3 dat2xml.py datafile -o 0.xml

   # use --help for further information
   python3 dat2xml.py --help
   usage: dat2xml.py [-h] [-o OUTPUT] [-f] input
   
   Convert a UISS input data file to a FLAME GPU 1.x initial states file. This is
   very brittle. The data file must contain the correct number of lines
   
   positional arguments:
     input                 UISS Datafile
   
   optional arguments:
     -h, --help            show this help message and exit
     -o OUTPUT, --output OUTPUT
                           path to output file
     -f, --force           Force overwriting of output files

Input File Mutation Script
==========================

As the UISS model is highly stochastic, many runs using different RNG seeds are required.

To avoid doing this by hand, a script was developed to automate this process.

Usage is as follows:

.. code-block:: bash

   python3 gendat.py --help                                                                                                                                                    
   usage: gendat.py [-h] [-f FILENAME] [-p PARAMETER [PARAMETER ...]] [-o OUTPUT]                                                                                              
                    [--list-parameters] [-v]                                                                                                                                   
                                                                                                                                                                               
   UISS Datafile modifier / Randomiser                                                                                                                                         
   
   optional arguments:
     -h, --help            show this help message and exit
     -o OUTPUT, --output OUTPUT
                           Directory for output files. Defaults to `.`
     --list-parameters     list the parameters of the program
     -v, --verbose         print verbose output
   
   required arguments:
     -f FILENAME, --filename FILENAME
                           template for the parameter file




.. note::

   This may be extended in the future to simplify parameter sweeps.

Output File Visualisation Script
================================

Along side the existing gnuplot script for visualising populations, a python script was developed to support the visualisations of many runs, and view the range of outputs capture. 

Usage is as follows:

.. code-block:: bash

   python3 uiss-plot.py --help
   usage: uiss-plot.py [-h] [-f FILES [FILES ...]] [-s MIN MAX] [-o OUTPUT]
                       [--verbose]
   
   Tool to plot one or more UISS output files as figure(s)
   
   optional arguments:
     -h, --help            show this help message and exit
     -f FILES [FILES ...], --files FILES [FILES ...]
                           Files to plot. One graph per passed argument
     -s MIN MAX, --shade MIN MAX
                           Min, max value pairs for shaded regions.
     -o OUTPUT, --output OUTPUT
                           path to output file
     --verbose             Verbose output



.. Output Set Comparison Script(s)
.. ===============================

.. To simplify and automate the comparison of simulators, a script was developed to compare directories of output files, and capture aggregate information to enable statistical comparison. 

.. Usage is as follows:

.. .. code-block:: bash

..    python3 uiss-compare.py --help
..    usage: uiss-compare.py [-h] -f FILES [FILES ...] [-o OUTPUT] --op
..                           {difference,between} [{difference,between} ...]
..                           [--verbose]
   
..    Tool to perform comparison operation(s) between two or more UISS output files,
..    producing one or more UISS output files
   
..    optional arguments:
..      -h, --help            show this help message and exit
..      -f FILES [FILES ...], --files FILES [FILES ...]
..                            Input files
..      -o OUTPUT, --output OUTPUT
..                            path to output directory/file?
..      --op {difference,between} [{difference,between} ...]
..                            Operations to perform.
..      --verbose             Verbose output


TUOS HPC Job Submission Scripts
===============================

Batch job submission scripts are used to submit jobs to HPC systems, such as ShARC and Bessemer at the university of Sheffield. 

Example submission scripts are provided for each job submission system.




SGE (ShARC)
-----------

.. note::

   Example job submission scripts are under development

Slurm (Bessemer)
----------------

.. note::
   
   Bessemer is not yet available for general purpose use. 

   Job submission scripts will be made available at a later date.



