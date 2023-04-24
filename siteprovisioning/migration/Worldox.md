# Worldox

Use the worldox tools to dump the matters from a single cabinet to a csv file. Definie a configuration object for each cabinet and use a seperate database for each cabinet import (not requried, but adviced for better performance)

Use the *Dump* option to analyze the csv file and dump the information to Excel.

Use the *Report* option to create a migration report. The excel file is stored in .\Migrate directory.

### Worldox Configuration

The mapping columns can also contain a filename (.txt) that should be stored in the migrate.exe directory. The mapping will be loaded from the external file. When a mapping is configured, the mapping information will be exported to Excel when using the

*CombineClientAndMatterCodeToTargetMatterCode*\
If left empty, the mattercode should be unique. The same mattercode is also used in Sharepoint.\
Specify *TRUE* to concatenate the clientcode and mattercode with no characters.\
Specify any other character(s) to concatenate the clientcode and mattercode with the configured character(s).

*MapFolders*\
Map a value to a specific (sub)folder

*MapUserNames*\
Map a value to a specific username/emailaddress

*MapClientCodes*\
Map a value to a specific clientcode

*MapClientMatterCodes*\
If CombineClientAndMatterCodeToTargetMatterCode is active, map the combined value to a specif mattercode else only the matter is replaced with a specifi mattercode

#### Mapping

*DocumentNumber*\
Specify the name of the sharepoint column where the document number (DocID column) will be stored

*DocumentNumberVersion*\
Specify the name of the sharepoint column where the document number (DocID column) and the original version will be stored

*PropertyToFolder*\
Select the property that should be converted into a folder. Use the *MapFolders* to map a value to a specific (sub)folder.

*FieldMapping*\
Optionally specify the sharepoint column name where the value Worldox should be stored in Sharepoint. Use the following fieldnames from the csv file:

- Field1 or 1
- Field2 or 2
- Field3 or 3
- Field4 or 4
- Field5 or 5
- Field6 or 6
- Field7 or 7
- Category
- Classified
- Cabinet
- Owner
- Comments
- Attributes
- Description

*MapFieldXToClientCode*\
Specify a number between 1-7 to specify the field that contains the clientcode (not required)

*MapFieldXToMatterCode*\
Specify a number between 1-7 to specify the field that contains the mattercode (required)

*MapFieldToCreatedBy*\
Specify a number between 1-7. If left empty or the value is empty the *Owner* field is used

*MapFieldToModifiedBy*\
Specify a number between 1-7. If left empty or the value is empty the *Owner* field is used

*MapCommentsToCheckinComments*\
If enabled use the comments as checkin comments for the migrated version

