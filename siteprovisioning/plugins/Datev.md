# Datev

This pugin will periodically query the Datev application api web service for new and updated clients (matters).

Copy the dll files from the Plugins\Datev directory to the site provisioning directory.  
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Datev plugin.

Specify the **Url**

For Basic Authentication specify the **Username** and **Password**. For NTLM Authentication do not fill these properties.

The following optional properties can be set:

**Client Code**
Json file property to match the sharepoint client code field, for example: organization_number.

**Client Name**
Json file property to match the sharepoint client name field, for example: organization_name.

**Client Field Mapping**
Optional field that maps json file client properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
For example: EstablishmentName=establishment_name|otherproperty

**Matter Code**
Json file property to match the sharepoint matter code field, for example: number.

**Matter Name**
Json file property to match the sharepoint matter name field, for example: name.

**Matter Field Mapping**
Optional field that maps json file matter properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
For example: MatterStatus=status|otherproperty
