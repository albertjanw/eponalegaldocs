# Client Matter Design

The following design implementation are supported. A default set can be configured for the Client and the Matter using the default *ClientSet* and *MatterSet* settings. The following order is used when resolving the (dynamic) name of set

- clientmatter*.json
- default client/matter set
- first defined set

## MatterSiteCollection

For each matter a new site collection is created with one or more document libraries. Nothing is created for the client.

Use the setting ConvertToGroupOrTeam to convert/create the matter sitecollection to an Office 365 group or Team. The setting can be set with a variable like {Groupify}. If the value can be convert to true, the existing sitecollection will be converted into a group/team (using the groupset configuration), for new matters a group/team is created. See <https://docs.microsoft.com/en-us/sharepoint/dev/transform/modernize-connect-to-office365-group#what-connecting-to-a-new-microsoft-365-group-does-to-your-site>

## MatterSite

For each matter a new site is created with one or more document libraries. Nothing is created for the client.

## MatterDocLib

For each matter a new document library is created. Nothing is created for the client.

## ClientSiteCollection_MatterSite

For each client a new site collection is created. For each matter a new site is created with one or more document libraries.\

Extend the client list with a column SiteURL (definition is equal to the SiteURL column in the matterlist). This column will be updated with the url where the client sitecollection is created and will be used for each new matter site for the client.

## ClientSiteCollection_MatterDocLib

For each client a new site collection is created. For each matter a new document library is created.\
Extend the client list with a column SiteURL (definition is equal to the SiteURL column in the matterlist). This column will be updated with the url where the client sitecollection is created and will be used for each new matter doclib for the client.

## ClientSite_MatterSite

For each client a new site is created. For each matter a new site is created with one or more document libraries.\
Extend the client list with a column SiteURL (definition is equal to the SiteURL column in the matterlist). This column will be updated with the url where the client site is created and will be used for each new matter site for the client.

## ClientSite_MatterDocLib

For each client a new site is created. For each matter a new document library is created.\
Extend the client list with a column SiteURL (definition is equal to the SiteURL column in the matterlist). This column will be updated with the url where the client site is created and will be used for each new matter for the client.

*SiteURL column*\

- create a single line column with internal name SiteURL

- specify column name formatting value

~~~json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "a",
  "txtContent": "@currentField",
  "attributes": {
  "target": "_blank",
    "href": "@currentField"
  }
}
~~~
