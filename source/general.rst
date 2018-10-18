Package
-------
When you download a Grouper package from the Download portal, you will receive a ZIP file containing the following 
files:

* ``CHANGELOG.md`` -- A file describing the version history of the Grouper software
* ``LICENSE-3RD-PARTY.txt`` -- A file containing the open source software licenses of all third-party software that
  is packaged as part of this Grouper distribution.
* ``README.md`` -- A short readme file
* ``java-grouper-{VERSION}-all.jar`` -- An executable JAR containing all referenced Java classes that are necessary to 
  run the grouper (including 3rd-party dependencies). Use this artifact if you want to use the grouper as an executable.
* ``java-grouper-{VERSION}.jar`` -- JAR without dependencies. Includes only the Java-Grouper classes. Use this artifact if 
  you want to use the grouper as a library and if you want to resolve the dependencies yourself.
* ``java-grouper-{VERSION}-javadoc.jar`` -- Contains the Javadoc files for the Grouper software.
* ``java-grouper-{VERSION}.pom`` -- Maven POM file stating the 3rd-party dependencies that are required by the Grouper 
  software.

.. note::
  Packages of 3rd-party dependencies in the executable JAR file are relocated in order to prevent version collisions
  with dependencies added by clients.

Specifications
--------------

The JavaGrouper groups patients into DRGs according to the SwissDRG "Specifications". These specifications represent a 
set of rules that define which patient is grouped into which DRG. The specifications are published three times a year in 
the `Download Portal <https://download.swissdrg.org/>`_.

Each specification is a set of JSON files contained in one folder. The folder is named

.. code-block:: java

  <major version>.<minor version>   // for SwissDRG   
  t<major version>.<minor version>  // for TARPSY     
    
where "major version" means either SwissDRG or TARPSY version (from 1 to currently 7 for the former);
"minor version" is a integer between 0 and 3:

- 0 = Catalog version
- 1 = Planning version 1
- 2 = Planning version 2
- 3 = Billing version

Examples:

- 7.3 = SwissDRG V7.0, Billing version
- t1.2 = TARPSY V1.0, planning version 2

In the Download Portal, there is a special `Zip archive <https://download.swissdrg.org/specs/28>`_
that contains all JSON specifications for SwissDRG versions V1.0 to V6.0.
  
The JSON specifications for the **newer versions** are also in the Download Portal under 
[Spezifikationen](https://download.swissdrg.org/specs): open the Zip archive of a given version and 
therein use the folder named e.g. 7.3 (meaning as described above).

.. note::
  The old C-Grouper used a binary format of the specifications (not JSON). These are also 
  included in the Zip archives of SwissDRG versions 1 to 7 (but not anymore in later versions).
    
Catalogs
--------

To calculate effective cost weights, the Java Grouper needs a catalog file: a list of 
DRGs (or "PCG", in the case of TARPSY) that contains for each DRG their cost weights, among other information.

The catalogs are CSV files, included in the ZIP archive of the specifications.                               
