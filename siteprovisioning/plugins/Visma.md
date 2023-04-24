# Visma

This pugin will periodically query the Visma api rest web service for new and updated projects (matters).

Copy the dll files from the Plugins\Visma directory to the site provisioning directory.  
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Visma plugin.

Specify the **Url**, **ClientID** and **Secret**. The Url should only contain the hostname.

The following optional properties can be set:

**Client Code**
Json file property to match the sharepoint client code field, for example: customer.number.

**Client Name**
Json file property to match the sharepoint client name field, for example: customer.name.

**Matter Code**
Json file property to match the sharepoint matter code field, for example: number.

**Matter Name**
Json file property to match the sharepoint matter name field, for example: name.

**Matter Field Mapping**
Optional field that maps json file matter properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
Leave empty for dynamic values config default
For example: SPProjectOwnerFirstName=projectOwner.firstName;SPProjectOwnerLastName=projectOwner.lastName|otherproperty

**MatterFilter**
Optional field to specify one or more filters in the format {visma field}={value}
