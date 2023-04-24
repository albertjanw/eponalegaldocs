# Create or update ClientMatter (excel)

Use this format to create or update one or more client/matters site/sitecollection/documentlibraries. The filename should contain *ClientMatter* and format is xls(x)

The following columns are required:

- ClientCode

- ClientName

- MatterCode

- MatterName

The following columns are optional. If missing or empty the default/first value from the configuration set is used.

- SharepointCfg

Use a different sharepoint configuration to handle this json file. Be careful with existing matters!

- MonitorDirectory\
Use a different monitor directory to handle this json file. Be careful with existing matters!

- ServerRelativeUrl\
Change the default url where new site/sitecollections are created

- ClientMatterDesign

See 3.8 for possible values (use the exact values as mentioned)

- ClientSiteCollectionSet

Only used if the design contains a client site collection

- ClientSiteSet

Only used if the design contains a client site or site collection

- ClientPermissionSet

Optionally specify permissionset for the matter (sitecollection or site)

- ClientDocLibSets

Only used if the design contains a client site or site collection. Not used yet!

- MatterSiteCollectionSet

Only used if the design contains a matter site collection

- MatterSiteSet

Only used if the design contains a matter site or site collection

- MatterOffice365GroupSet\
Only used if the design is office 365 group

- MatterPermissionSet

Optionally specify permissionset for the matter (sitecollection/site)

- MatterDocLibSet/MatterDocLibSets\
Only used if the design contains a matter site, site collection or document library. Specify one or more values using ; or , as a separator. If design is *DocLib* only the first specified value is used.

- MatterDocLibPermissionSet/MatterDocLibPermissionSets\
Optionally specify permissionset for the matter doclib. Specify one or more values using ; or , as a separator.

- MatterListItemPermissionSet\
Optionally specify permissionset for the matter listitem in the matterlist.

- MatterDocLibFolderSets\
Only used if the design contains a matter site, site collection or document library. Specify one or more values using ; or , as a separator.

- MyMattersList\
Only used if a new matter sitecollection, site or document library is created. Specify one or more usernames using a ; as separator. An entry is added to the My Matterslist for matter and the specified users.

If a MonitorDirectory is specified, this setting is only used if the matter is new (doesn't exist in the matterlist) or if the Url column value starts with 'http'. Move the file to monitor directory.

If a SharepointCfg is specified, this setting is only used if the matter is new (doesn't exist in the matterlist) or if the Url column value starts with 'http'. Use the monitor directory for the sharepoint configuration where the matterlist is stored!

Other columns in the sheet are used as meta-data fields. The column header should match the internal-name or title of the sharepoint column/field.

If the meta data is only valid for the client, use the prefix *Client.* (with the dot). For example: Client.AccountManager.

If the meta data is only valid for the matter, use the prefix *Matter*. (with the dot) or no prefix. For example: Matter.MatterType or MatterType

If the meta data is only valid for matchings sets and should not be used for default values, use the prefix *\_\_* (double underscore). For example: \_\_User

When one or more rows are not correctly handled (for example missing user, etc.) at the end a new excel file is created inside the error directory, containing only the rows with an error. The error column contains the reason of the error. For more details, check the error.log. Fix the errors and move the file from the error directory into the monitor directory.

If the URL column in the matterlist for the matter is empty, the executed actions are handled the same as for new matters.
