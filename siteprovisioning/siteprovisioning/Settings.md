# Settings

## Provisioning

- MyMattersListColumnName

Specify one or more variables names (; separated (no comma!!!) ) that are used to add an entry to the My Matters List when a new matter is created.

- Matter Status

Specify a column name that holds the matter status. If one of values specified in the *Closed Values* setting are filled in, the matter is identified as closed. For closed matters some actions are not executed anymore like:

- Creating a matter list entry

- Creating a new site(collection)/doclib/office 365 group

- Create new parts inside an existing site(collection)/doclib/office 365 group

Metadata will be updated.

*Csv*\
The fileformat for files that are dropped in the monitor directory can also be the cvs format. Specify the delimiter in the setting CsvDelimiter. Double quotes can be used as a field value separator, but are optional.\
Sample:

\"Epona\";\"Epona;Legal\"

Will be parsed as two columns:\
Epona\
Epona;Legal

## Provisioning Extranet

If enabled, an extra matter is created in the matter list and the initial matter has a reference to the extranet matter. The settings for extranet can be set via *Settings, Provisioning, Extranet*:

If ClientListExtranetColumnNameCreate and/or MatterListExtranetColumnNameClientCreate and/or MatterListExtranetColumnNameMatterCreate are not empty, extranets will be optionally created.

ClientListExtranetColumnNameCreate\
Create an extranet for the client if the value of the column name in the client list can be converted to true. It's also possible to specify a value of \<true\> / yes, ja in this setting, resulting in always creating an extranet for the client.

MatterListExtranetColumnNameClientCreate\
Create an extranet for the client if the value of the column name in the matterlist can be converted to true. It's also possible to specify a value of \<true\> / yes, ja in this setting, resulting in always creating an extranet for the client.

MatterListExtranetColumnNameMatterCreate\
Create an extranet for the matter if the value of the column name in the matterlist can be converted to true. It's also possible to specify a value of \<true\> / yes, ja in this setting, resulting in always creating an extranet for the client.

The mattercode for the extranet is stored in the columname that is configured via the settings ClientListExtranetColumnNameMatterCode, MatterListExtranetColumnNameClientMatterCode and/or MatterListExtranetColumnNameMatterMatterCode.

!! At this moment the column name to store the matter can only have one value, ExtranetMatterCode. If both ClientExtranet and MatterExtranet are enabled, the reference that is stored with the initial matter is the matter extranet !!

***Client***

The mattercode for the extranet for the client will be stored in the client list, using the fixed (internal) column name *ExtranetMatterCode*. Optionally you can add this column to the matterlist, using the additional column feature of the *Client* lookup column.

ExtranetClientDesign\
Specify the design that should be use for the (extranet) matter for the client.

ClientClientDesignSet\
Specify the name of the *Set* that contains the settings for the client part of the provisioning (only used for design ClientSiteCollection_MatterSite, ClientSiteCollection_MatterDocLib, ClientSite_MatterSite, ClientSite_MatterDocLib).

ClientMatterDesignSet\
Specify the name of the *Set* that contains the settings for the matter part of the provisioning.

ClientMatterCodeFormat\
Specify the mattercode for the extranet matter. Use variables, for example *ClientCode}EX* for a Client extranet. Make sure it's a unique matter code!

ClientMatterNameFormat\
Specify the mattername for the extranet matter. Use variables, for example*{ClientName}* for a Client extranet.

ClientSharepointUrlSite\
Optionally specify an alternative url where the extranet matter should be created.

ClientSharepointUrlDocLib\
The url is created in the external sharepoint environment. Specify the dynamic full url of the doclib, for example:\
[https://sp.sharepoint.com/sites/{MatterCode}/documents](https://sp.sharepoint.com/sites/%7bMatterCode%7d/documents)

***Matter***

ExtranetMatterDesign\
Specify the design that should be use for the (extranet) matter for the client.

ClientDesignSet\
Specify the name of the *Set* that contains the settings for the client part of the provisioning (only used for design ClientSiteCollection_MatterSite, ClientSiteCollection_MatterDocLib, ClientSite_MatterSite, ClientSite_MatterDocLib).

MatterDesignSet\
Specify the name of the *Set* that contains the settings for the matter part of the provisioning.

MatterCodeFormat\
Specify the mattercode for the extranet matter. Use variables, for example *{MatterCode}EX* for a Matter Extranet. Make sure it's a unique matter code!

MatterNameFormat\
Specify the mattername for the extranet matter. Use variables, for example *{MatterName} (Extranet)*

SharepointUrlSite\
Optionally specify an alternative url where the extranet matter should be created.

SharepointUrlDocLib\
The url is created in the external sharepoint environment. Specify the dynamic full url of the doclib, for example:\
[https://sp.sharepoint.com/sites/{MatterCode}/documents](https://sp.sharepoint.com/sites/%7bMatterCode%7d/documents)

When the extranet matter should be created externally, for example with a local on premise sharepoint and an sharepoint online for extranet purposes. A local matter list entry is created with the calculated url where the extranet is located.

ExternalMonitorDirectory\
Specify the monitor directory that is linked with external sharepoint environment

ClientSharepointUrlDocLib / SharepointUrlDocLib\
The url is created in the external sharepoint environment. Specify the dynamic full url of the doclib, for example:\
[https://sp.sharepoint.com/sites/{MatterCode}/documents](https://sp.sharepoint.com/sites/%7bMatterCode%7d/documents)

ClientSharepointUrlSite / SharepointUrlSite\
The url is created in the external sharepoint environment. Specify the dynamic full url of the site, for example:\
[https://sp.sharepoint.com/sites/{MatterCode}](https://sp.sharepoint.com/sites/%7bMatterCode%7d/documents)

## Create additional Matterlist entry in other environment

Via the setting *MatterListMonitorDirectory* you can specify a monitor directory where a matterlist\*.json file is dropped with the matterlist properties from the created/updated client/matter. This can be used to create a reference in another matterlist to the url of this client/matter.

## Update metadata on documents

Via the setting *UpdateDefaultValuesOnDocumentsMonitorDirectory* you can specify a monitor directory when a AssignDefaultValuesInDocLib\_\*.json file is dropped with the properties from the created/updated client/matter. This handler will update all the documents inside the document library. Use a separate site prov. instance for this action. This update can take a long time and potentially block other handlers to execute.
