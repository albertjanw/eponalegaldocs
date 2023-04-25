# Move or rename files

Use this format to move or rename one or more files. The filename should contain *MoveFile* and format is xls(x)

The following columns can be defined:

- ClientCode (optional)
- MatterCode
- SourceFile
- TargetClientCode (optional)
- TargetMatterCode (optional)
- TargetFile

In SP2013/2016 it's not possible to move a file to a different doclib/site/sitecollection, Export, import and delete the file is currently necessary. The source and targetfile can contain a serverrelative url (start with /) or use the url relative to the document library (without using a starting /)

In SP Online the file can be moved to a different doclib/site/sitecollection. If the file is moved to a different doclib/site/sitecollection, also specify the TargetMatterCode.
