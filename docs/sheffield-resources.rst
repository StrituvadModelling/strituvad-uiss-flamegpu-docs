.. _sheffield_resources:

****************************************
Resources at the University of Sheffield
****************************************

The University of Sheffield (TUOS) has several HPC facilities which can be used as a part of the Strituvad project for running simulations, including CPU and GPU resources.

The facilities are namely `ShARC <http://docs.hpc.shef.ac.uk/en/latest/sharc/>`_ and `Bessemer <http://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html>`_.


Gaining Access: TUOS Staff
==========================

Members of staff at the University of Sheffield can gain access to HPC systems by emailing helpdesk@sheffield.ac.uk.

To access private GPU nodes, please contact p.richmond@sheffield.ac.uk.


Gaining Access: External Users
==============================

Project members who are not members of the University of Sheffield require a University of Sheffield computing account to access these resources.
Individuals must register for an `External UCard and Computing Account <https://www.sheffield.ac.uk/cics/ucards/external>`_ by completing the `relevant form <https://www.sheffield.ac.uk/polopoly_fs/1.168944!/file/externalformCURRENT.pdf>`_. 
Once complete please email this to p.richmond@sheffield.ac.uk.


Connecting to the Clusters
==========================

To connect to TUOS HPC facilities, you must either be on campus, or connected to the university of Sheffield VPN. 

To connect to the VPN, please follow the `instructions provided by CiCS <https://www.sheffield.ac.uk/cics/vpn>`_.

It is then possible to connect via SSH. Please see the `Sheffield HPC Docs for further information <http://docs.hpc.shef.ac.uk/en/latest/hpc/connecting.html>`_.


Transferring Files
==================

Please see the `Sheffield HPC Docs for information on transferring files to and from the HPC clusters <http://docs.hpc.shef.ac.uk/en/latest/hpc/transferring-files.html>`_.


ShARC
=====

`ShARC <http://docs.hpc.shef.ac.uk/en/latest/sharc/>`_ is one of the University of Sheffield HPC Clusters, optimised for multi-node computing. 

ShARC also contains some `GPU nodes <http://docs.hpc.shef.ac.uk/en/latest/sharc/GPUComputingShARC.html>`_, notably. K80 GPUs in the public queue, and P100 GPUs in various private queues.
For the purposes of the Strituvad project the private GPU queues can be made available.

ShARC uses the Son of Grid Engine Scheduler (SGE). Details on how to make use of this scheduler can be found on the `Sheffield HPC Documentation <http://docs.hpc.shef.ac.uk/en/latest/hpc/scheduler/submit.html#submit-queue>`_.


Bessemer
========

`Bessemer <http://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html>`_ is one of the University of Sheffield's HPC clusters, optimised for single-node or high-throughput computing.

Bessemer contains `1 public GPU node containing 4 V100 GPUs <http://docs.hpc.shef.ac.uk/en/latest/bessemer/cluster_specs.html#gpu-node-specifications>`_, but will also contain many private V100 nodes, which will be made available for the Strituvad project.

Bessemer uses the Slurm Scheduler. Details on how to make use of this scheduler can be found on the `Sheffield HPC Documentation <http://docs.hpc.shef.ac.uk/en/latest/hpc/scheduler/submit.html#submit-queue>`_.



