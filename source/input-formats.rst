.. _input-formats:

Input Formats
=============

The Batchgrouper is capable of accepting a range of input formats. In the following sections, we provide links
to documentations of the various formats. 

BFS Format
----------

This format has been developed by the `Swiss Federal Statistical Office <https://www.bfs.admin.ch/bfs/en/home.html>`_. 
The documentation for this format is available at 
`https://www.bfs.admin.ch/bfs/de/home/statistiken/gesundheit/erhebungen/ms.html <https://www.bfs.admin.ch/bfs/de/home/statistiken/gesundheit/erhebungen/ms.html>`_.

SwissDRG Batchgrouper Format 2017
---------------------------------
The revised batchgrouper format defined as of 2017 is documented in 
`https://docs.swissdrg.org/BatchgrouperFormat2017.pdf <https://docs.swissdrg.org/BatchgrouperFormat2017.pdf>`_.

This format includes medication information and therefore supports full supplement grouping for both CHOP and ATC based
supplements.

URL Format
----------
As of grouper version ``1.1.0``, the ``URL`` format is exactly the same as the Batchgrouper Format 2017, with
the only difference being that some characters are replaced with characters that are safe to be included in an URL:

* ``;`` is replaced with ``_``
* ``|`` is replaced with ``-``
* ``:`` is replaced with ``$``

Due to the similarity with the Batchgrouper Format 2017, this format also supports full supplement grouping for both 
CHOP and ATC based supplements. Use this format if you need to store the state of a patient case in an URL.

SwissDRG Batchgrouper Format
----------------------------

The legacy Batchgrouper format is documented in 
`https://docs.swissdrg.org/grouper-doku-de.pdf <https://docs.swissdrg.org/grouper-doku-de.pdf>`_.

.. note:: 
  This format does not include medications. Supplement grouping with this format will only consider
  supplements with respect to CHOP codes. For supplement grouping that includes ATC based supplements, 
  please consider using the SwissDRG Batchgrouper Format 2017.