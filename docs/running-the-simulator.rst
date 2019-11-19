.. _running_the_simulator:

*********************
Running the Simulator
*********************

To run the FLAME GPU UISS simulator, the code must first be compiled to be executed on an NVIDIA GPU.

See the `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_ contains more precise requirements and instructions.

Requirements (Linux)
====================

+ CUDA 8.0 or greater
+ GCC 7 or greater
+ xsltproc
+ xmllint
+ make 
+ git


To run FLAME GPU simulations a Compute Capability 3.0 or greater Nvidia GPU is required, with an appropriate CUDA driver.


Compilation
===========

To build the executable, navigate into the relevant source directory and run `make console`.

Other options are available, as described in the `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_. 


Running the Simulator
=====================

FLAME GPU Console mode simulations take several arguments as follows:

.. code-block:: bash

   usage: FLAMEGPU_UISS [-h] [--help] input_path num_iterations [cuda_device_id] [XML_output_override]

Where

+ input_path corresponds to an input xml file, typically called 0.xml. This should contain the model parameters.
+ num_iterations is the number of iterations for the simulator to run. For UISS this should be set to 0, as the number of iterations is related to several input parameters, and calculated at runtime.
+ `cuda_device_id` controls which GPU should be used in a multi-GPU system. Typically the value of 0 should be used.
+ XML_output_override controls how often a FLAME GPU XML output file is produced. This has significant performance impact and is not required for the UISS implementation. Use the value `0`.

I.e. 

.. code-block:: bash

    ./bin/linux-x64/Release_Console/FLAMEGPU_UISS iterations/0.xml 0 0 0 

Output files will be produced in the same directory as `0.xml`, i.e. `iterations/` in the above example.

Tools
=====

Several scripts and tools have been developed to simplify the running of the model. See :ref:`tools`. for further information.
