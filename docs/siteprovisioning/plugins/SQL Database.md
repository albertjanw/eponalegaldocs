# SQL Database

Copy the Epona.Database.dll from the Plugins\\Database directory to the site provisioning service directory. Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the database plugin.

One or more jobs can be defined. Each job will be start every X minutes, configured via the IntervalInMinutes parameter. If a \@LastRunDateTime parameter is available in the commandtext, the value from the configuration will be used and updated with the current datetime.

Specify a full connectionstring.

- Sql user:
server=sql;database=aderant;user id=cms;password=cms
- Windows Authentication\
server=sql;database=aderant;Trusted_Connection=True\
the current windows user is used when runnning in console mode or the service account is used to connect to the sqlserver when running as a service.

or specify the name of the connectionstring that is specified in the Epona.SiteProvisioning.exe.config. Use this option when a specific provider is necessary (other than the SqlClient). See <http://www.connectionstrings.com> for samples.

Specify the sql commandtext or a full path to a file that contains the sql commandtext. Use the parameter \@LastRunDateTime to inject the last run date from the configuration.

It's also possible to dynamically use not default ADO.NET providers. Follow these steps:

- search on <https://www.nuget.org/> for the provider and click on Download Package
- rename the nupkg file to zip and extra the files
- browser to \<zip\>/lib/net45 / 46, unlock the dll and copy the dll to the site provisioning directory
- specify the name of the dll in the *providername* setting

If you get a "type X not found exception", update the *providername* setting with the correct name of DbFactoryType type in the format *\<dll name\>;\<type name\>*

The column names returned by the query are mapped on the clientmatter handler, see 3.20.2. If the column name starts with Client. (client dot) or Client\_\_ (double underscore) or Matter. (matter dot) / Matter\_\_ (double unscore) the name / value is added to the client or matter properties (without the prefix). Unknown properties are added to the matterproperties with a \_\_ and are only used for dynamic fields.
