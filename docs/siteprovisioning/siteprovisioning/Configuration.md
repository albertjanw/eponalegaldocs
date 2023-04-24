# Configuration

Start the Configurator.exe to create one or more configuration objects. Each object contains a monitor directory and a sharepoint configuration object. Files that are dropped in the specific monitor directory are executed using the linked configuration file.

Use the configurator tool to create/modify the settings.

Create named sets of settings. Via the Excel or the json file the named configuration sets can be referenced.

WARNING ! Don't change the *Name* of a configuration item, if it's already referenced in another set. (if needed find/replace the name directly in json).

## ServerRelativeUrl

Specify one or more url's where new sitecollections/sites are created. For example: `/sites.`\
Use ; as a separator to specifiy multiple url's, like `/sites/dms1;/sites/dms2`. The site provisioning service will create the new site or doclib in the sitecollection/site with the least items (sites/doclibs), als known as "round robin"

It's also possible to use variables. For example: `/sites/DMS-{GroupCode}-01;/sites/DMS-{GroupCode}-02`
