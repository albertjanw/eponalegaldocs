# Sharepoint Client / MatterList monitor

This plugin will periodically query the SharePoint client and/or matterlist in DMSforLegal for new and updated clients/matters/listitems.

Copy the dll files from the Plugins\\MatterList directory to the site provisioning directory.\
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Client / MatterList plugin.

The plugin will schedule a job using the interval in minutes, start and end datetime properties. After each run the LastRunDate is updated. Only created or changed matters (via the modifydate) after that time are converted to json files and dropped in the monitor directory.

Additional columns can be added to let the user specify custom permissions on the matter (*ColumnPermissions_Contributor, ColumnPermissions_Editor, ColumnPermissions_Reader).* Create the columns as a multi user column type. Make the field empty to reassign the default permissionset.

The matterlist supports creating of sub/sub matters by adding "Parent MatterCode" column. Specify the name of the column in *Column_ParentMatterCode*. If there's a value, this mattercode will be searched in in the matterlist and a submatter/site is created in the parent matters site.

## Client Extranet

The client list reader can be enabled to support matters that are created for a Client using the Extranet feature (and configuration). If enabled the client list will be monitored for changes and if the client extranet configuration is enabled a new matter is created for the client.

Create a column yes/no in the clientlist (for example with a default value yes) and specify the column name in the *ClientListExtranetColumnNameCreate*.

Create a  new column in the client list with the (internal)name *ExtranetMatterCode* and specify that name in the *ClientListExtranetColumnNameMatterCode*
