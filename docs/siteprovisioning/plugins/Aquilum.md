# Aquilum

This plugin will periodically query the Aquilum application api web service for new and updated jobs (matters).

Copy the dll files from the Plugins\Aquilum directory to the site provisioning directory.  
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Aquilum plugin.

Specify the **url**, **username** and **password**.

Enable the **TestMapping** option to validate the result json files. The LastRunDateTime property is not updated and the result json files are saved in the Monitor/Test directory.

The following optional properties can be set:

**MapMatterCode**
Column name in Aquilum API for matter code. By default it uses "IdJob", but can be set to other column like "JobCode"

**MatterIdColumnName**
Sharepoint column to map MatterId

**MatterJobCodeColumnName**
Sharepoint column to map Matter JobCode

**MatterNameOriginProfesionalColumnName**
Sharepoint column to map NameOriginProfesional

**MatterNamePpalManagerColumnName**
Sharepoint column to map NamePpalManager

**MatterNameSecundaryManagerColumnName**
Sharepoint column to map NameSecundaryManager

**MatterDescrActivityColumnName**
Sharepoint column to map DescrActivity

**MatterOfficeColumnName**
Sharepoint column to map Office

**MapClientCode**
Column name in Aquilum API for client code. By default it uses "IdClie", but can be set to other column like "ClientCode"

**ClientIdColumnName**
Sharepoint column to map ClientId

**DefaultClientCode**
Default client code if Aquilum client code is empty

**DefaultClientName**
Default client name if Aquilum client name is empty

**MatterAreaColumnName**
Sharepoint column to map Area

**MatterCloseDateColumnName**
Sharepoint column to map CloseDate

**MatterRegisterDateColumnName**
Sharepoint column to map RegisterDate

**MatterStatusColumnName**
Sharepoint column to map Status. The value returned from Aquilium can be replaced with a value from DynamicFieldValue mapping using the name `Aquilium.Status`.

The plugin will schedule a job using the interval in minutes, start and end datetime properties. In the first run, it will set LastRunDate to "1900-01-01" (YYYY-MM-DD) to fetch all records from Aquilum API. After each run the LastRunDate is updated. Only created or changed matters after that time are converted to json files and dropped in the monitor directory.
