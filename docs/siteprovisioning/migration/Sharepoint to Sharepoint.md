# Sharepoint to Sharepoint

Copy the files from the \\Plugins\\Migrate\\Sharepoint directory.

Start the migrate tool, a new tab is visible. Click on ... button to create or edit an migrate configuration. The configuration is stored in the \\Config\\Sharepoint directory.

To prevent duplicate folder imports (when custom foldermapping is used), all the folders in the source document library are intially loaded. Sharepoint Search is used to quickly fetch all folders. Be careful with recent folder changes and wait until the search index is updated before starting an migration

## Sharepoint Configuration

Specify the *SourceTargetSharepointName* that contains the source files. The files are migrated to the selected Sharepoint configuration in the migrate tool.

The source files can be specified with an mattercode (existing DMSFL environment) or using an url.

**MatterCode**\
<sourcemattercode\>=\<targetmattercode\>/\<newtargetfolder\>

If the targetmattercode is empty, the sourcemattercode is also used in the target DMSFL environment

Optionally specify a new targetfolder in the target DMSFL environment (use / or \\ as separator)

**Url**\
Check the box "MatterCode is Url"\
<url\>=\<targetmattercode\>/\<newtargetfolder\>

The url can be specified as:\

- Site, migrate all document libraries\
- Doclib, migrate the document library and subfolder(s)\
- Folder, migrate the folder and subfolder(s)

During the import a duplicate (sub)folder mapping will be detected and imported only once.

Optionally specify a new targetfolder in the target DMSFL environment (use / or \\ as separator)

**ImportFolderPermissions**\
If enabled, the permissions from the source folder are migrated to the targetfolder, but only if the targetfolder doesn't exist in the target document library.

**FieldMapping**\
Specify the internal names of the columns in the format:\
sourceColumnName=targetColumnName

## Replace TargetFolder

The relative folder path (relative to the doclib) can be remapped using
the *ReplaceFolder* settings.

Specify a source (path) and targetpath to change the mapping. Use a
fixed name \_\_SKIP\_\_ (double underscores) to skip the migration of
the folder and subfolder(s). Use a ; or a new line to add multiple
mappings.

Use a fixed name \_\_ROOT\_\_ (double underscore) to map (only) the rootfolder to another folder.

Samples:

- =Documents\
 Migrate all files in the root and all subfolders to the subfolder
 Documents

- E-Mails=Emails\
 Migrate all files and subfolders in E-Mails to the subfolder Emails

- =Documents;\_\_ROOT\_\_=Documents\
 Migrate all files from the rootfolder to the Documents folder and all other (sub)folders also to the (relative)Documents folder.

- =Documents;Emails;Docs=Documents\
 Migrate all files in the root and all subfolders except for Emails
 and Docs to the Documents folder. Move Emails to the Emails folders
 and Docs to the Documents subfolder

- =Migrate;Emails/Attachments=\_\_SKIP\_\_\
 Migrate all files in the root and all subfolders except for
 Emails/Attachment to the Documents folder. Skip the files in the
 Emails/Attachment and subfolder(s).

## Dump Content

The user displayname can be different in the sitecollection. The result excel file contains a list of the users in the rootsite collection and optionally the site collection specified from the matters that are specified.

Also the custom security is dumped to the sheet for sites, doclibs, folders and documents (only for items that don't inherit permissions).

An excel file is created and stored in the
\\Migrate\\Sharepoint\<name\>\_\<date\>.xlsx.

```Document security is not imported when the azure migration is enabled.```

The tab Folder/Document security can be copied to a new excel file. After manual validation the file can be imported by dropping the file in the monitor directory with the name "PermissionSet*.xlsx".
