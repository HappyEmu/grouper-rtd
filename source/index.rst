.. SwissDRG Grouper Documentation documentation master file, created by
   sphinx-quickstart on Fri Oct 12 12:52:07 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

SwissDRG Grouper Documentation
==============================
The JavaGrouper 1.2.0 is a reimplementation of the older C based grouper kernel. 
The grouper logic remains the same. However there are some differences to the old grouper kernel, especially 
regarding non-functional features:

- The new grouper kernel is fully based on Java and hence platform independent.
- The new grouper kernel supports concurrent grouping of patient cases. Once loaded, a grouper kernel
  can be used in concurrent environments without further measures.
- The old binary grouper specifications can no longer be used. The specifications will be released 
  using a more open JSON based format.
- The semantics for flagging used variables has slightly changed and been simplified. As used flags 
  have been relevant in the PCCL algorithm prior to SwissDRG 3.0, this new behavior can lead to different grouping 
  results in rare cases (< 1 in 100'000) for SwissDRG systems 1.0 and 2.0.
- The Same Day Flag (SDF) has been removed as it was never relevant for grouping and was not properly 
  entered in most setups. As a consequence the grouper kernel is no longer able to calculate an entry 
  date based on the exit date and the length of stay. Hence the grouper cannot calculate an age based 
  on an exit date, the length of stay and a birth date.

Getting Started
---------------

Download
^^^^^^^^
If eligible, you can download the Grouper software from the `Download Portal <https://download.swissdrg.org>`_ provided 
by SwissDRG AG. Please refer to the `Grouper homepage <https://www.swissdrg.org/de/akutsomatik/grouper>`_ if you need
more information about the Grouping software and about how to get access to the Download portal.

In the following sections, we provide a user guide for users of the grouper software.

.. toctree::
   :maxdepth: 3
   :caption: General

   general

.. toctree::
   :maxdepth: 3
   :caption: Batchgrouping

   batchgrouping
   input-formats
   output-format

.. toctree::
   :maxdepth: 2
   :caption: Grouper Library

   grouper-library
