# CobolToXml
This project will convert **Cobol Data Files** to/from **Xml** using a *Cobol Copybook*.

It uses:

* cb2xml - Cobol Copybook analysis project ~ https://github.com/bmTas/cb2xml
* JRecord - Read Cobol data files from java using a Cobol Copybook ~ https://github.com/bmTas/JRecord

Usage:

  In jave you can use a Fluent interface to 
  
~~~java  

          // ***  Convert Cobol data file to Xml ***
          // *-------------------------------------*
          
        JRecordConstantVars constants = Cobol2Xml.JR_CONSTANTS;
	
        Cobol2Xml.newCobol2Xml("G:/Users/Bruce01/RecordEditor_HSQL/CopyBook/Cobol/DTAR020.cbl")


                                         // Cobol Options
                         .setFileOrganization(constants.IO_FIXED_LENGTH)
                         .setDialect(constants.FMT_MAINFRAME)               
                         .setSplitCopybook(constants.SPLIT_NONE)      
                         .setFont("cp037")

              .cobol2xml("G:/Users/Bruce01/RecordEditor_HSQL/SampleFiles/DTAR020.bin", 
                         "G:/Users/Bruce01/RecordEditor_HSQL/SampleFiles/DTAR020.bin.xml");

 
          // ***  Convert Xml to Cobol Data file ***
          // *-------------------------------------*

        Cobol2Xml.newCobol2Xml("G:/Users/Bruce01/RecordEditor_HSQL/CopyBook/Cobol/DTAR020.cbl")

                                         // Cobol Options
                         .setFileOrganization(constants.IO_FIXED_LENGTH)
                         .setDialect(constants.FMT_MAINFRAME)               
                         .setSplitCopybook(constants.SPLIT_NONE)      
                         .setFont("cp037")

              .xml2Cobol("G:/Users/Bruce01/RecordEditor_HSQL/SampleFiles/DTAR020.bin.xml",
                         "G:/Users/Bruce01/RecordEditor_HSQL/SampleFiles/DTAR020byJava.bin");

~~~                         

You can also use the older (and more limited) batch interface

~~~
    java -jar ../lib/Cobol2Xml.jar -cobol Xmpl.cbl -fileOrganisation text  ^
                                 -split 01 ^
                                 -recordSelection FIRST-TYPE       REDEFINES-RECORD-TYPE=T1 ^
                                 -recordSelection SECOND-TYPE      REDEFINES-RECORD-TYPE=T2 ^
                             -input  In.txt   ^
                             -output out1.xml 
~~~