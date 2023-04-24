# Assign permissions PermissionSet

Use this format to (re-)assign permissions to a sharepoint object. The filename should contain *PermissionSet* and format is xls(x)

The following columns can be defined:

- Url (optional)

- SiteUrl (optional)

- MatterCode (optional)

- ObjectUrl (optional)

- Folder (optional)

- PermissionSet (optional)

- ResetPermission (optional)

- ReAssignPermission (optional)

- RemoveCurrentPermission (optional)

- DisableInheritance (optional)

- CopyRoleAssignments (optional)

- DomainMembers.\<permissionrole\> (optional)

- Groups.\<permissionrole\> (optional)

If Url is specified, the siteurl / objecturl / clientcode / mattercode are ignored. The url should contain the relative url to the object (web/folder/document/listitem) that should be changed.

If SiteUrl is specified:\
Use the objecturl to be sure that the correct object is changed. If ObjectUrl is empty the permissions on the site are changed. The Folder column is ignored.

If MatterCode is specified:\
Use the objecturl to be sure that the correct object is changed (relative to the site url)\
If ObjectUrl is empty the Folder column is used. In a single document library setup, the Folder column can point to a folder inside the doclib (relative to the doclib). In a multi document library setup the Folder should include the document library url or use the ObjectUrl.\
If the Folder is empty, the site permissions are updated. Use a single / or \\ to update the doclib permissions.

The optional colums ResetPermission, ReAssignPermission, RemoveCurrentPermission, DisableInheritance and CopyRoleAssignments override the values in the PermissionSet from the configuration.

If RemoveCurrentPermission = true, all the current permissions are removed from the current object (file/folder/etc) and the specified permissions are re-assigned.

If Resetpermissions = true, the current permissions are removed and resetted before assigning the new permissions from the permissionset. ! USE WITH CARE, ALL CHILD OBJECTS ARE ALSO RESETTED !

Optionally add more columns when variables are used inside the name / users / groups inside the permissionset.

If a PermissionSet is specified, the optional DomainMembers/Groups columns are ignored. If no PermissionSet is specified, the DomainMembers/Groups columns can be used to apply a customer permissionset. Use the the syntax: DomainMembers.\<PermissionsRole\> or Groups.\<PermissionRole\> the column should contain one or more user/groupnames or sharepoint groupnames (using ; or , as separator). *The CopyRoleAssignments is set to true for the newly created permissionset.*

Example: "DomainMembers.Contribute"

Permissions on the matters list are NOT modified when you this handler. Use the MatterList handler to update the permissions on the listitem or move the listitem to another folder in the [Matters List](../matterlist/Create%20or%20update%20items%20in%20MatterList.md#create-or-update-items-in-matters-list)
