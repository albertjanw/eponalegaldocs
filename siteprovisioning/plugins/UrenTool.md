# UrenTool

This plugin will periodically query the UrenTool application api web service for new and updated projects (matters).

The plugin will schedule a job using the interval in minutes, start and end datetime properties.

Copy the dll files from the Plugins\Urentool directory to the site provisioning directory.  

Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the UrenTool plugin.

Specify the **url** (only the host, for example <https://epona.api.finance.atabase.nl/>) and **BearerToken**

The following optional properties can be set:

**ProjectCaluclationModelColumnName**
Sharepoint column to map project calculation_model field ('cost_based','intern', 'fixed')

**ProjectResponsibleEmployeeNameColumnName**
Sharepoint column to map project responsible_employee name field

**ProjectBillerEmployeeNameColumnName**
Sharepoint column to map the project biller_employee name field

**ProjectStatusColumnName**
Sharepoint column to map the project status field ('open', 'closed')

**ProjectTypeColumnName**
Sharepoint column to map project project_type field

**DefaultClientCode**
Default client code if UrenTool client code is empty

**DefaultClientName**
Default client name if UrenTool client name is empty
