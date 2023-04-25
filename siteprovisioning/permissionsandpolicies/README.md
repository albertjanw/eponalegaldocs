# Assign permissions PermissionSet (Json)

Use this format to (re-)assign permissions to a sharepoint object. The filename should contain *PermissionSet* and format is json.

The following columns can be defined:

- SiteUrl (optional)

- MatterCode (optional) (/ClientCode)

- ObjectUrl (optional)

- Folder (optional)

- PermissionSet (optional)

- ResetPermission (optional)

- ReAssignPermission (optional)

- RemoveCurrentPermission (optional)

- DisableInheritance (optional)

- CopyRoleAssignments (optional)

- Roles

If Permissionset is specified the permissionset is loaded from the sharepoint config and overruled with settings from the json. If empty a new permissionset is created.

If Roles are specified in the json the roles from the permissionset are ignored.

If SiteUrl is specified:\
Use the objecturl to be sure that the correct object is changed. If ObjectUrl is empty the permissions on the site are changed. The Folder column is ignored.

If MatterCode is specified:\
Use the objecturl to be sure that the correct object is changed (relative to the site url)\
If ObjectUrl is empty the Folder column is used. In a single document library setup, the Folder column can point to a folder inside the doclib (relative to the doclib). In a multi document library setup the Folder should include the document library url or use the ObjectUrl.

The optional colums ResetPermission, ReAssignPermission, RemoveCurrentPermission and DisableInheritance override the values in the PermissionSet from the configuration.

If Resetpermissions = true, the current permissions are removed and resetted before assigning the new permissions from the permissionset. ! USE WITH CARE !

Optionally add more columns when variables are used inside the name / users / groups inside the permissionset.
