.. _output-format:

Output Format
=============

DRG File
--------

Supplements File
----------------

Das Zeilenformat für die Ausgabedatei der Zusatzentgelte (ZE) ist wie folgt::

    ID;TOTAL_AMOUNT;SUPPLEMENTS

Die Kürzel sind in der nachfolgenden Tabelle kurz erläutert:

.. csv-table::
   :header: "Spalte", "Beschreibung"
   :widths: auto
   :align: center

   ``ID``, "Fallschlüssel (Primary Key)"
   ``TOTAL_AMOUNT``, "aufsummierter Gesamtbetrag aller berechneten Zusatzentgelte"
   ``SUPPLEMENTS``, "Liste von ZE-Strukturen"

Eine einzelne Zusatzentgelt-Struktur ist folgendermassen kodiert: ``ze_id:ze_code:ze_amount``.

.. csv-table::
   :header: "Feld", "Beschreibung"
   :widths: auto
   :align: center

   ``ze_id``, "Bezeichner des ZE gemäss Fallpauschalenkatalog"
   ``ze_code``, "Auslösender Code (CHOP oder ATC Code)"
   ``ze_amount``, "Betrag des ZE gemäss Fallpauschalenkatalog"

Beispiel
^^^^^^^^
.. code-block:: text
    
    ...
    1234;12257.05;ZE-2018-02.02:3995C2:2502.95|ZE-2018-21.03:990512:8056.15|ZE-2018-52.06:J06BA02_IV_nr:1697.95
    ...
