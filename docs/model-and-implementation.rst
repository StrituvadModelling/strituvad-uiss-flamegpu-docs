.. _model_and_implementation:

************************
Model and Implementation
************************


The model is based on UISS 6.0, developed and provided by Francesco Pappalardo et Al. at the University of Catania. 

The current implementation is built using a modified version of FLAME GPU 1.5, which imposes some restrictions on how much of the original model can be directly reproduced (to be addressed with a FLAME GPU 2 implementation).


Model
=====

The model contains agents located at discrete locations within a toroidal, hexagonal lattice. 
Each lattice site contains quantities of chemicals, and some lattice-site behaviours occur (such as diffusion). 

The agents include:


+ BCell
+ THelper
+ TCytotoxic
+ DendricCell
+ EpiteliaCell
+ MCell
+ PlasmaCell
+ NKCell
+ ICList
+ AntibodyList
+ AntigenList

.. + LatticeSite
.. + AntigenComposition


Implementation
==============

The current implementation is based on UISS 6.0, using a modified version of FLAME GPU 1.5.0

FLAME GPU
---------

`FLAME GPU <http://flamegpu.com>`_ is a high performance Graphics Processing Unit (GPU) extension to the FLAME framework for Agent Based Modelling (ABM). 
It provides a mapping between a formal agent specifications with C based scripting and optimised CUDA code. 

Users formally describe the model using the XMLModelFile (following provided XML Schema) and implement behaviours in CUDA C, using the pragmatically generated API. This abstracts the complexities of GPU programming away from the modeller.

FLAME GPU is open source, and can be found on github at  `FLAMEGPU/FLAMEGPU <https://github.com/flamegpu/flamegpu>`_.

Documentation is also host both on github at `FLAMEGPU/docs <https://github.com/flamegpu/docs>`_ and online at `http://docs.flamegpu.com/en/master/ <http://docs.flamegpu.com/en/master/>`_.


Modifications
^^^^^^^^^^^^^

To enable the model to be implemented using FLAME GPU, modifications were made to FLAME GPU to enable certain behaviours not previously required by FLAME GPU models.

Currently these are implemented in a branch of a separate repository (`uiss-6 branch in ptheywood/flamegpu <https://github.com/ptheywood/FLAMEGPU/tree/uiss-6>`_), as they are not yet ready for general purpose use.


XMLModelFile
------------

The XMLModelFile.xml in the `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_ is the formal definition of the model.
It contains:

+ Parameters of the Model
+ Agent descriptions
+ Message List definitions
+ Agent behaviour descriptions
+ Directed Acyclic Graph (DAG) of per-iteration behaviour

.. @todo - once the improved DAG visualisation script is merged in, add instructions for use / include the diagram?.

Functions Files
---------------

As the model is complex, rather than using a single CUDA C file, functions.c, for all agent behaviour implementation, it is split across several implementation files (.h, .c, .cuh, .cu), in the src/model/ directory.
Further information can be found in the `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_.



Input File
----------

FLAME GPU simulations expect and XML file describing the initial state of the simulation as an input file. 

For the UISS implementation, this is an XML formatted version of the UISS 6 input file format. This can be converted automatically using one of the provided tools·


Output Files
------------

The FLAME GPU UISS implementation aims to match the output of the FLAME GPU 


Limitations
-----------
Due to the nature of the GPU implementations, and limitations of the current version of FLAME GPU, not all of the UISS features can be replaced exactly.

For instance, the order of interactions is not shuffled on subsequent iterations. The `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_ contains further information on the limitations of the implementation.

Further Information
-------------------

Further information can be found within the `source repository <https://github.com/StrituvadModelling/strituvad-uiss-flamegpu>`_, containing non-public information.
