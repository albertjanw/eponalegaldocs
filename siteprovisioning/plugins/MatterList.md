# MatterList plugin

This plugin will monitor the matterlist for new/changed items. Each new/changed item is converted to a json file and dropped in the monitor folder.

Copy the dll files from the Plugins\MatterList directory to the site provisioning directory.  

Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the MatterList plugin.

## Filter

If a filter is specified only items that match the filter are exported. One or more fields can be used to specify a filter. By default the filter is executed as "AND". Start the filter with "OR " to specify an OR filter. It's not yet possible to group filters or use a combination of and/or. You can use the | (pipe character) to specify an OR filter within the same field.\
Use ; to specify more filters. If none of the filters have a match on the matter, the matter is skipped.

Check the json export file for the correct fieldnames.\
The properties and values are matched with case-insensitivity.\
Use the fixed values \_\_EMPTY\_\_ or \_\_NOTEMPTY\_\_ (double underscores suffix and prefix) to compare an empty/not empty value.\
Use the \* character at the begin and/or end for a partial match.

Examples:

- ClientCode=2022_*\
export all items where the clientcode starts with 2022_
- ClientCode=*_2022\
export all items where the clientcode ends with _2022
- ClientCode=\*2022\*\
export all items where the clientcode contains 2022
- MatterProperties.Status=OPEN\
export all items where the matterproperties, status value equals Open.
- MatterProperties.Status=OPEN|CLOSED\
export all items where the matterproperties, status value equals Open or Closed.
- MatterProperties.External=true;MatterProperties.Status=OPEN|CLOSED\
export all items where the matterproperties, External property is true AND the status value equals Open or Closed.
- OR MatterProperties.External=true;MatterProperties.Status=OPEN|CLOSED\
export all items where the matterproperties, External property is true OR the status value equals Open or Closed.

If you want to filter on columns SiteUrl or Url, add a new calculated column, return the different values (use string values to allow more variants in the future) and configure a filter on that calculated column using the above syntax.
