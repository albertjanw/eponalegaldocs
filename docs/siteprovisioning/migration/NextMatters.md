# NextMatters

Import one or more matters from NextMatters to Sharepoint. If no matters are specified all matters are imported.\
The files are imported from the filesystem. During the migration the additional meta-data is loaded from the NextMatters database (if a matching file is found).

### NextMatters Configuration

*Db Server / Database / Username / password*\
Specify the database connection to the NextMatters database.

*SourceDirectory*\
Specify the root directory where the physical files are stored, the parent directory of the *{year}\\{matters}* folder.

*ReplaceFolders*\
Map a specific value to a (sub)folder. Map an empty value with a new directory to move files without a folder into a specific folder. (for example "=Documents")

*MapUsers*\
Map a specific value to an emailaddress/username that can be found in Sharepoint.

### NextMatters Dump

Use the dump function to analyze the content of the database. The specified matters (or all) are exported to a excelsheet. For each mattercode the following is exported:

- mattercode
- sourcedirectory
- number of files
- size of files

The sheet *FileOwners* contains the owners that are extracted from the files stored on the filesystem. Map the windows username to a sharepoint username/emailaddress and update the *MapUsers* configuration.

The sheet *Medewerkers*  contains a list of all users that are stored in NextMatters. The email column is used in Sharepoint to find a matching user. Use the *MapUsers* configuration if that's not correct (or update NextMatters).

### Migrate

Specify the matters that should be imported. The physical location for the matter will be extracted from the database. If no matters are specified all matters are imported.\
For each file in the matter (sub)directory, the database will be checked if the file exists. If not, import the file with only the metadata from the filesystem (owner, create/modifydate) and (mapped)folder. If the file is found in the database it will use the metadata from the database. If multiple versions of the file are found in the database, the unique nextmatters documentnumber will be added to the imported filename to make a unique filename. Each version will be converted into a Sharepoint version. Test
