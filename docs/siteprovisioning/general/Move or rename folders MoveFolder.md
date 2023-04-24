# Move or rename folders MoveFolder

Use this format to move or rename one or more files. The filename should contain *MoveFolder* and format is xls(x)

The following columns can be defined:

- Url (optional)

- ClientCode (optional)

- MatterCode (optional)

- SourceFolder

- TargetFolder

In SP2013/2016 it's not possible to move a folder to a different doclib/site/sitecollection, Export, import and delete the file is currently necessary.\
Specify a Mattercode, the docliburl is fetched from the matterlist and the sourceFolder and targetfolder are relative paths inside the doclib (do not start with a / ).\
OR\
Specify an url to a doclib. The sourceFolder and targetfolder are relative paths inside the doclib (do not start with a / ). (necessary in a multi-doclib design)

In SP Online the folder can be moved to a different doclib/site/sitecollection.\
Specify a relative sourceFolder and TargetFolder (start with a / ) and leave mattercode/url empty\
OR\
Specify a Mattercode, the docliburl is fetched from the matterlist and the sourceFolder and targetfolder are relative paths inside the doclib (do not start with a / ).\
OR\
Specify an url to a doclib. The sourceFolder and targetfolder are relative paths inside the doclib (do not start with a / ). (necessary in a multi-doclib design)
