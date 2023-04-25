# Create or update items in Matters List

Use this format to create/update items in the matter list. The filename should contain *MatterList* and format is xls(x)

The following columns can be defined:

- ClientCode

- ClientName

- MatterCode (required)

- MatterName

- Title (required)

- PermissionSet

- Folder

- ... additional columns are mapped on the matter list column names

If (dynamic) name of the permissionset is specified and matterlist security is enabled (via folders or item level permissions) the security from the permissionset is applied.

If Folder is specified the listitem is moved to the (existing) folder.

If Title is specified, the title formatting for the mattername in the configuration is ignored.

If MatterName is not specified the mattername and title are not updated.

If ClientCode and ClientName are specified, the clientlist is also updated with (new) values ClientCode and ClientName.

To update the MatterCode with a new value, specify the original value in the MatterCode column and add a column with the name *\_\_Code\_\_*  (double underscores!) and the new MatterCode.

If a permissionset is specified, the listitem permissions are always executed (if enabled in the permissionset), ForceUpdate = true. If variables are used, be sure to add them to the excel file.
