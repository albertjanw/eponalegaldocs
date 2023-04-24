# Legalsense

This plugin will periodically query the legalsense application for new and updated matters.

Copy the dll files from the Plugins\\Legalsense directory to the site provisioning directory.\
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Legalsense plugin.

Specify the url, username and password.

The plugin will schedule a job using the interval in minutes, start and end datetime properties. After each run the LastRunDate is updated. Only created or changed matters after that time are converted to json files and dropped in the monitor directory.

Userproperties are cached for 2 days. Restart the site provisioning service for a refresh.

UseMatterName, if enable force the plugin to use matter *name* field and not the matter *display* field.

**Parent Client**\
The parent client can be imported into the client list via the setting *Parent Client Columnname*. If empty or equal to the client, an empty value will be set. Enable the setting *ClientParentClientNameUseClientIfEmpty* to set the client name as value for an empty value.

**MatterStatus**\
Legalsense contains two fields for the matter status:

- softkill_status, possible values are 1 = open, 2 = archived, 3 = removed\
\
Specify the sharepoint columname in the *MatterStatusColumnName* setting and the values *MatterStatusValueForArchived* and *MatterStatusValueForOpen*

- matterstatus, lookup list in legalsense\
\
Specify the sharepoint columname in the *MatterStatusFieldColumnName* setting.

**Chinese wall kind**\
The field chinese wall kind contains a numeric (system defined) value in LegalSense. Ask the LegalSense support department for the possible values implemented for a specific client. Create a field mapping value to map it to a string value in SharePoint.\

**Store Sharepoint url in customField**\
After the matter is created/updated in Sharepoint the Doclib Url can be stored in a custom field in Legalsense. Specify the name of the custom field (type is url in Legalsense). The UI in Legalsense will show a clickable link to Sharepoint.

**Filter**\
Define one or more filters if not all matters should be created or updated in SharePoint. Use the format ```ls_fieldname=value;```.
For example:\
```chinese_wall_kind=1|3```\
Only matters with chinese_wall_kind = 1 OR 3 are valid. Use | (pipe character) as a separator for multiple values.

See [MatterList Filter](MatterList.md#filter) for more samples.

Possible fieldnames and values:

```text
"aml_required": null,
"archive_number": "",
"archived_date": null,
"billing_instructions": null,
"billing_user": "/api/v1/user/4887/",
"can_archive": true,
"chinese_wall_kind": 1,
"client": "/api/v1/client/8237/",
"client_reference": "",
"court_reference_number": "",
"created_date": "2013-06-26T00:00:00",
"custom_fields": {
    "DMSforLegal": ""
},
"date": "2013-06-26",
"description": "",
"display": "Client/Matter",
"docket_number": null,
"engagement_letter_sent": null,
"firm": "/api/v1/firm/1/",
"id": 19475,
"insolvency_number": null,
"invoice_language": "nl-nl",
"is_billable": null,
"is_recofa": false,
"legal_aid_number": "",
"magistrate": null,
"matter_status": "/api/v1/matter_status/1/",
"matter_type": "/api/v1/matter_type/2/",
"modified_date": "2013-06-26T00:00:00",
"name": "Client/Matter",
"number": "2013.25576",
"office_expenses_rate": "5.00",
"originating_user": "/api/v1/user/4887/",
"points": null,
"practice_area": "/api/v1/practice_area/15/",
"practice_group": "/api/v1/practice_group/63/",
"real_archive_number": "",
"reduction_rate": null,
"referrer": "/api/v1/referrer/2/",
"resource_uri": "/api/v1/matter/19475/",
"rvr_approval_date": null,
"softkill_status": 1,
"supervising_user": "/api/v1/user/4887/"
```

For custom fields, use syntax: ```custom_fields.name=123```

For reference fields like (practice_area, supervising_user, etc) specify the full "api reference value", see samples above. For example: ```practice_area=/api/v1/practice_area/15/```  (where 15 is the internal ID of the practice area).

To filter on an empty value use the magic string ```__EMPTY__``` (double underscore), for example ```archived_date=__EMPTY__```.

To filter on an non empty value use the magic string ```__NOTEMPTY__``` (double underscore), for example ```archived_date=__NOTEMPTY__```.
