# OpenText

Copy the Files from the \\Plugins\\Migrate\\OpenText directory.

Start the migrate tool, a new tab is visible. Click on ... button to create or edit an OpenText configuration. The configuration is stored in the \\Config\\OpenText directory.

Azure migration is not yet supported.

## OpenText Configuration

- DocumentTypeToContentTypes

The DocumentType can be mapped to a contenttype in sharepont. Specify one or more items using the following syntax:

\<DocumentType\>=ContentType

If a match is found, that contenttype is used. If no match is found, the specified default content type is used, see DefaultDocumentContentType (or else the default contenttype from the doclib is used (or the configured Email contenttype for an email file))

It's also possible to specify an external text filename, use the extension .txt. Copy the content to a text file and specify a the file path relative to the installation directory in the setting.

- Users/Groups

The username and groupname can be converted into a sharepoint username/group. Use the ReplaceUserGroupNames setting in the Sharepoint
config, section Settings. If that mapping contains an empty mapping with a default username, that username is used when the user is not found in Sharepoint.

It's also possible to specify an external text filename, use the extension .txt. Copy the content to a text file and specify a the file
path relative to the installation directory in the setting.
