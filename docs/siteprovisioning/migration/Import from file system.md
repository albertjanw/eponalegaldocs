# Import from file system

To upload files into sharepoint create a mapping file in the Excel. The
excel file should contain the following fields:

- SourceFile\
a full path reference to a file (full control ntfs permissions
required)

- SourceDirectory\
a full path reference to a directory (full control ntfs permissions
required)

- ClientCode (optional)

- DocLibUrl

- MatterCode

- TargetFolder

SourceFile or SourceDirectory is required.

If a SourceDirectory is specified the complete directory including
subdirectories is uploaded, recreating the original subdirectories in
sharepoint. All other columns are applied to all the files and directory
(like contenttype/permissionset, etc.). It's possible to 'remap'
subdirectories by adding a separate entry in the excel file for that
specific directory.

An external SqLite database is used to track the file import for delta
migrations. Use an external browser to view the contents of the
database, like <http://sqlitebrowser.org/>

DoclibUrl or MatterCode is required. ClientCode is only necessary if
mattercodes are not unique.

Optionally the following columns can be used:

- PermissionSet\
Specify the name of a permissionset from the config

- ContentType

Specify the name of a contenttype, if empty the default contenttype in
the doclib is used.

- DocumentVersion

Remove this column if the version should be parsed from the filename.
This column can be used to set a version or override the version from
the filename.

- DocumentName\
This value is used as the filename in Sharepoint instead of the
physical filename from disk. When the documentname is equal for two
or more files in the same *TargetFolder* (and doclib), multiple
versions are imported using the *DocumentVersion* column.

- CheckinComments\
This value contains optional version comments that are used to
checkin the document

- Additional columns are parsed as meta-data

When the export is finished a Result excel file is created with all the
files that uploaded without errors. If there are any errors an
additional Error excel file is created with only the files that are not
uploaded. The Error column contains a short message about the error. The
log file contains all the details of the errors. After fixing the errors
the Error file can be used to restart the import action.

When a file is successfully imported a \*.url file is created. This file
contains the url where the file is uploaded and the current last
modified date of the imported file. When the import is restarted a delta
import is executed using the information from the url file.\

- No Url file\
file is new, create a new file with unique name in sharepoint\
- Existing url\
modify date in the url file is equal to the lastwrite stamp of the file,
skip file import else import the file as a new version and update the
url file with the lastwrite stamp of the file.

## Configuration

TargetFolders

See 6.4.2, Replace TargetFolder

## Dump Directories

Use this function to extract a matter number from the directoryname.

Create an excel file that contains the mattercodes (on the first tab). If no MatterCode column header is found, all rows in the first column are assumed to contain a mattercode.

After specifying the root directory in the filesystem, the tool will scan every subdirectory and export the subdirectory to an excel file and include the mattercode in a separate column if a matternumber is found in (a part) of the directory name. Optionally skip the directory that already contains exported files.

- Mattercode is equal to directoryname

- Directoryname starts with or ends with the following separators \<space\> \_ - \# @ \<dot\> in combination with a matternumber

- Directoryname contains a matternumber in combination with the following separators \<space\> \_ - \# @ \<dot\>

- Directoryname contains (matternumber) or \[matternumber\] (with or without additional spaces)

The NewTargetFolder column contains the calculated targetcolumn that will be used when importing into Sharepoint.

The Matched sheet contains the top-level folders with a MatterCode.

The Not Matched sheet contains the top-level folders without a MatterCode.

## Dump Files

Use this function to export all files in a directory structure. Optionally skip all files that are already exported (using the \*.url
shortcut files). Create an excel file that contains the mattercodes to automatically fill in the mattercode from the directory name (see Dump directories). The targetfolder column is filled in relatively to the parent directory that contains a mattercode.

## Dump NTFS Permissions

Use this function to export all NTFS permissions from one or more (sub-)directories. Create an Excel with the following columns:

- SourceDirectory\
 a full path reference to a directory

- ClientCode (optional)

- MatterCode

The MatterCode (and optionally clientcode) is used to get the documentlibrary Url from Sharepoint. Subdirectories of the *SourceDirectory* are mapped as subfolders inside the documentlibrary (relative).

After clicking on dump permissions, optionally include files with not inherited permissions and/or optionally create a site entry to  specify Read permissions on the site.

The result Excel files contains all the NTFS permissions mapped on the current Url in sharepoint.

Optionally specify a replace user/group name in the Settings of the site provisioning configurator to replace a windows domain username with an Office 365 online username. Leave the mapping empty to ignore the user/group.

## Analyze

Use this option to analyze an import excel file for duplicate entries. It will create a new excel file that only contains an unique combination of client/mattercode together with a sourcedirectory without a sub-sourcedirectory that points to the the same client/mattercode.

