# Webserver

The service can optionally accept http requests. The service will listen to requests to the port that is specified in the Epona.SiteProvisioning.Service.exe.config. Use 0 or empty to disable this feature.

To test this behavior start a browser and browse to the [http://\<servername:\<port\] site. The ApiKey is used for identification and to specify the correct configuration.

Currently two methods are supported:

- Post a json ClientMatter structure to the url /ClientMatter
- Post a Sharepoint ListItem as a json string (key/value) to the url /SPListItem
