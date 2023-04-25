# Cicero

This plugin will periodically query the Cicero application for new and updated matters.

Copy the dll files from the Plugins\\Cicero directory to the site provisioning directory.\
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Cicero plugin.

Specify the url (hostname), clientid and secretkey.

The plugin will schedule a job using the interval in minutes, start and end datetime properties. After each run the LastRunDate is updated. Only created or changed matters after that time are converted to json files and dropped in the monitor directory.

## Store Sharepoint in Cicero

After the matter is created/updated in Sharepoint the sharepoint information can be stored in Cicero. This can be disabled by setting the config *StoreSharepointInfoInCicero* to false.

## Filter

Define one or more filters if not all matters should be created or updated in SharePoint. Use the format ```cicero_fieldname=value;```. Use ; to specify more filters. If the filters have no match on the matter (using AND criteria), the matter is skipped.\
For example:\
```status=Open```

See [MatterList Filter](MatterList.md#filter) for more samples.

Possible fieldnames and values:

```json
{
    "id": 75095,
    "name": "Deco-Nova/Maas",
    "number": "00000102",
    "reference": "00000102",
    "clientName": "DECONOVAWEERTBV",
    "clientCode": "93256",
    "status": "Closed",
    "ownerMailAccount": "",
    "openingDate": "2009-11-26T09:00:00+01:00",
    "closingDate": "2019-07-30T09:00:00+02:00",
    "customFields": []
},
```

For custom fields, use syntax: ```custom_fields.name=123```

To filter on an empty value use the magic string ```__EMPTY__``` (double underscore), for example ```closingDate=__EMPTY__```.

To filter on an non empty value use the magic string ```__NOTEMPTY__``` (double underscore), for example ```closingDate=__NOTEMPTY__```.
