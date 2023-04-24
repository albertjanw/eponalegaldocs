# CaseManager

This plugin will periodically query the sharepoint CaseManager application for new and updated cases.

Copy the dll files from the Plugins\\CaseManager directory to the site provisioning directory.\
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the CaseManager plugin.

Specify the siteurl to the casemanager application.

The plugin will schedule a job using the interval in minutes, start and end datetime properties. After each run the LastRunDate is updated. Only created or changed matters after that time are converted to json files and dropped in the monitor directory.

## Field mapping

Specify the (internal) field name from the *Case* list and specify the target fieldname in the Matters List. For example:\
MatterCode=CaseNumber;MatterName=Title

**Matter**
The ExternalIdentifier and Title field from the *Case* list are used for the MatterCode and MatterName. Specify a different mapping in the Fieldmapping if needed (reference internal fieldnames from the case manager case list)

**Client**
The ExternalIdentifier and Title field from the *Case Client* list are used for the ClientCode and ClientName. Specify a different mapping in the Fieldmapping if needed (reference internal fieldnames from the case manager client list). For example:\
ClientCode=ExternalIdentifier;ClientName=Title;

**DefaultClientCode/Name**
If no client is used or set for the case, specify a default value that should be used. (Client is required in the Matters list)
