.. _tools:

*****
Tools
*****

Several scripts / tools have been developed to simplify the use of the simulator, which can be found in the `StrituvadModelling/strituvad-uiss-flamegpu repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_. 

Further information and examples of all these scripts can be found in the `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_.


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

ShARC (and Iceberg) at the University of Sheffield use the SGE job submission system.

The tools sub-repository contains example job submissions scripts to compiler the FLAME GPU UISS implementation, and run the 5 example datafiles.

Alternatively it is possible to use interactive sessions.


Compilation via SGE
'''''''''''''''''''

Compilation via SGE can occur using the ``tools/sge/compile.sharc.sh`` job submissions script.

.. code-block:: bash

   # Navgate to the tools/sge directory
   cd strituvad-uiss-flamegpu/tools/sge/
   # Submit the batch job to compile the code
   qsub compile.sharc.sh
   # Ensure that the job has finished before running the model
   qstat


Alternatively this can be ran within an interactive sesssion.

.. code-block:: bash

   # Get an interactive session, no GPU required
   qrshx
   # Navgate to the tools/sge directory
   cd strituvad-uiss-flamegpu/tools/sge/
   # Run the compilation script
   ./compile.sharc.sh

.. note:: 

   Compilation does not require a GPU.

Execution via SGE
'''''''''''''''''

To run an example, once the executable has been compiled (see above) the appropriate job submission script can be submit.

I.e. for the ``datafile_1`` example, with a single invocation of a single seed

.. code-block:: bash

   # Navgate to the tools/sge directory
   cd strituvad-uiss-flamegpu/tools/sge/
   # Submit the batch job to compile the code
   qsub datafile_1.sharc.sh


Alternatively this can be executed in a GPU interactive session, although this is not reccomended.

.. code-block:: bash

   # Get a GPU interactive session (in the private queue for this project on ShARC)
   qrshx -l gpu=1 -P rse-strituvad
   # Navigate to the SGE directory
   cd strituvad-uiss-flamegpu/tools/sge/
   # Run the appropriate script (or runs the commands contained within manually)
   ./datafile_1.sharc.sh

This will place generated ``.out`` files in the ``iterations/datafile_1`` directory, which can be retrieved using scp.


.. code-block:: bash

   # From your local machine, replacing $CICS_USERNAME with your cics username
   scp -r $CICS_USERNAME@sharc.shef.ac.uk:~/strituvad-uiss-flamegpu/simulator/iterations/datafile_1/\*.dat path/to/local/destination



Checking job progress via SGE
'''''''''''''''''''''''''''''

To check the progress of your jobs on SGE, use the ``qstat`` command

.. code-block:: bash

   qstat


Slurm (Bessemer)
----------------

.. note::
   
   Bessemer does not yet contain the private GPU nodes we will be using.

   Job submission scripts will be updated to reflect this at a later date.



Bessemer at the University of Sheffield use the Slurm job submission system.

The tools sub-repository contains example job submissions scripts to compiler the FLAME GPU UISS implementation, and run the 5 example datafiles.

Alternatively it is possible to use interactive sessions.


Compilation via Slurm
'''''''''''''''''''''

Compilation via slurm can occur using the ``tools/slurm/compile.bessemer.sh`` job submissions script.

.. code-block:: bash

   # Navgate to the tools/slurm directory
   cd strituvad-uiss-flamegpu/tools/slurm/
   # Submit the batch job to compile the code
   sbatch compile.bessemer.sh
   # Ensure that the job has finished before running the model
   squeue -u $USER


Alternatively this can be ran within an interactive sesssion.

.. code-block:: bash

   # Get an interactive session, no GPU required
   srun --pty bash -i
   # Navgate to the tools/slurm directory
   cd strituvad-uiss-flamegpu/tools/slurm/
   # Run the compilation script
   ./compile.bessemer.sh

.. note:: 

   Compilation does not require a GPU.

Execution via Slurm
'''''''''''''''''''

To run an example, once the executable has been compiled (see above) the appropriate job submission script can be submit.

I.e. for the ``datafile_1`` example, with a single invocation of a single seed

.. code-block:: bash

   # Navgate to the tools/slurm directory
   cd strituvad-uiss-flamegpu/tools/slurm/
   # Submit the batch job to compile the code
   sbatch datafile_1.bessemer.sh


Alternatively this can be executed in a GPU interactive session, although this is not reccomended.

.. code-block:: bash

   # Get a GPU interactive session
   srun --pty bash -i --gres=gpu:1 --partition=gpu
   # Navigate to the slurm directory
   cd strituvad-uiss-flamegpu/tools/slurm/
   # Run the appropriate script (or runs the commands contained within manually)
   ./datafile_1.bessemer.sh

This will place generated ``.out`` files in the ``iterations/datafile_1`` directory, which can be retrieved using scp.


.. code-block:: bash

   # From your local machine, replacing $CICS_USERNAME with your cics username
   scp -r $CICS_USERNAME@bessemer.shef.ac.uk:~/strituvad-uiss-flamegpu/simulator/iterations/datafile_1/\*.dat path/to/local/destination


Checking job progress on Slurm
''''''''''''''''''''''''''''''

To check the progress of your jobs via slurm, use the ``squeue`` command

.. code-block:: bash

   squeue -u $USER



