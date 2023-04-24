# Create SiteCollection(s)

Use this format to create new sitecollection without an entry in the client or matterlist. The filename should contain *SiteCollection* and format is xls(x)/csv.

The following columns can be used:

- Code (required)

- Title (required)

- SiteCollectionSet (if empty, use first)

- Url (if empty, use from sharepoint configuration)

- DocIDPrefix (optionally, if empty use *Code*)

- Update

A new or existing site collection is updated at the location {Url}/{Code} with the configuration loaded from the sitecollectionset/cfg.

Existing site collections are handled as new and all updates are applied. To disable this behaviour set *Update* to true and only existing site collection are handled as updates and only update actions are applied.
