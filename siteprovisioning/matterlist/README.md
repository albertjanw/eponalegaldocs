# Create or update item in MatterList (Json)

Use this format to create/update a single matter list item in the matter list. The filename should contain *MatterList* and format is json.

The following columns can be defined:

- ClientCode

- ClientName

- MatterCode (required)

- MatterName (required)

- Title

- PermissionSet

- Folder

- ... additional columns are mapped on the matter list column names

If (dynamic) name of the permissionset is specified and matterlist security is enabled (via folders or item level permissions) the security from the permissionset is applied.

If Folder is specified the listitem is moved to the (existing) folder.

If Title is specified, the title formatting for the mattername in the configuration is ignored.

If ClientCode and ClientName are specified, the clientlist is also updated with (new) values ClientCode and ClientName.
