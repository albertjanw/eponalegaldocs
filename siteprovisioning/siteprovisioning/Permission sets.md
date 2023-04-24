# Permission sets

By default permissions are only assigned when the object is created.

Set the *ReAssignPermissions* property to true to change the permissions of existing objects. The permissions on already created objects will be re-assigned in the next run. The site provisioning will store an unique identifier in the web object. If the key doesn't exists or the permissions set has changed the permissions will be reassigned. To force an update without changing the permissions update the *Name* to a different value.

Specify a *Name* and RoleType *None* to create a custom permission level.

If *ResetPermissions* is true, inheritance is enabled and **ALL** custom permissions assigned to all (nested) child objects are also reset. **!! Use with care !!**

If *DisableInheritance* is true and the object has inherted permissions, the *CopyRoleAssignments* and *RemoveCurrentPermissions* are used to Break the role inheritance, see [Microsoft Site](<https://msdn.microsoft.com/query/dev14.query?appId=Dev14IDEF1&l=EN-US&k=k(Microsoft.SharePoint.Client.SecurableObject.BreakRoleInheritance);k(TargetFrameworkMoniker-.NETFramework,Version%3Dv4.5);k(DevLang-csharp)&rd=true>)

If *RemoveCurrentPermissions* is true, the current assigned permissions are removed before adding the new permissions.

The Matter List can contain folder with specific permissions to protect the matter name for viewing when a user is searching the matter list. Use the setting *MatterListFolderName* to specify a foldername. When the PermissionSet is applied the matter list item is potentially moved to the specified folder. Optionally use dynamic names to use a value from a column in the matterlist. This will only work with the permissionset that is applied on the matter. Set *MatterListFolderEnabled* to true to enable this.

When *MatterListItemPermissionsEnabled* is enabled, the permissionset is applied to the single listitem. The permissionset can be specified in the json and/or plugins (using dynamic name matching).

To use the built-in groups for AssociatedOwnerGroup, AssociatedVisitorGroup and AssociatedMemberGroup use the fixed groupname: \_members, \_owners or \_visitors
