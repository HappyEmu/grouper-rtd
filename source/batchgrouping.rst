Batch Grouping
--------------

There should be some code:

.. code-block:: java

  package org.swissdrg.grouper.example;

  import org.swissdrg.grouper.Catalogue;
  import org.swissdrg.grouper.EffectiveCostWeight;
  import org.swissdrg.grouper.GrouperResult;
  import org.swissdrg.grouper.IGrouperKernel;
  import org.swissdrg.grouper.IGrouperReader;
  import org.swissdrg.grouper.IPatientCaseParser;
  import org.swissdrg.grouper.PatientCase;
  import org.swissdrg.grouper.PatientCaseParserFactory;
  import org.swissdrg.grouper.PatientCaseParserFactory.InputFormat;
  import org.swissdrg.grouper.SpecificationReader;
  import org.swissdrg.grouper.WeightingRelation;

  import java.util.Map;

  public class ApiExample {

      private static final String WORKSPACE_FOLDER = "/home/madonna/spec-6av";
      private static final String CATALOGUE_FILE   = "/home/madonna/catalogue60.csv";

      public static void main(String[] args) throws Exception {

          // "BATCH" is the input parser format; alternatives: "URL" for a UrlPatientCaseParser, "BFS" for a BFSPatientCaseParser
          IPatientCaseParser parser = PatientCaseParserFactory.getParserFor(InputFormat.BATCH);

          // Input string in the Batch grouper input format as described in https://docs.swissdrg.org/grouper-doku-de.pdf
          String inputLine = "123456;75;0;;W;01;00;9;0;;M179;M0694;I1090;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;815421:L:20151026;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;";

          PatientCase patient = parser.parse(inputLine);

          IGrouperReader reader = new SpecificationReader();
          IGrouperKernel grouper = reader.loadGrouper(WORKSPACE_FOLDER);

          // see java-grouper-1.0.0-javadoc/org/swissdrg/grouper/IGrouperKernel.html#groupByReference-org.swissdrg.grouper.PatientCase-
          grouper.groupByReference(patient);

          GrouperResult result = patient.getGrouperResult();

          Map<String, WeightingRelation> catalogue = Catalogue.createFrom(CATALOGUE_FILE);

          System.out.println("DRG: " + result.getDrg());
          EffectiveCostWeight ecw = EffectiveCostWeight.calculateEffectiveCostWeight(patient, catalogue.get(result.getDrg()));
          System.out.println("ECW: " + ecw.getEffectiveCostWeight());

          /** should print:
           *
           *    DRG: I43B
           *	  ECW: 19650
           *
           */
      }
  }
