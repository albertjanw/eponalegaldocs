# Legal Tracker

This plugin will register a CSV handler to convert the exported CSV files from LegalTracker to valid client matter json files. The filename should contain *LTtoiManageMatterUpdates*

The LegalTracker csv files should be dropped into the monitor directory and are converted to clientmatter\*.json files using the mapping from the configuration.

*FieldMappingClientCode/Name*\
If the csv file contains a clientcode/name column, specify the fieldname in the FieldMappingClientCode/Name

*DefaultClientCode/Name*\
If the csv file doesn't contain a clientcode/name column, specify the default value for the ClientCode/Name

*FieldMappingMatterCode/Name*\
Specify the name of the field van the MatterCode/Name

*FieldMappingMatterUser*\
Specify the name of the field that contains the username that should have access to this matter. You can optionally specify the name of the field in Sharepoint/variable to be used in the permissionset. For example:\
User=\_\_Members\
this will use the value from *User* column in the csv file and fill the MatterProperties in the json with the key \_\_Members and ; separated the usernames from the rows in the csv file.

*FieldMappingMatter*\
Specify the mapping of additional fields in the format of: csv field=sharepoint field. The values will be added to the matterproperties in the json file with the sharepoint field name as key.
