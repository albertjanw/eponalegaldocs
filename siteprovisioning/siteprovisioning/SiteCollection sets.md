# SiteCollection sets

**FormatUrl**\
By default the *MatterCode* is used as the url for the new sitecollection. Optionally specify a dynamic name to change the url, for example:

- DMS\_{MatterCode}

- /teams/DMS\_{MatterCode}

If the the UrlFormat starts with a / the default *ServerRelativeUrl* is ignored.

## Team Site

Change the *SiteDesign* to Team. A modern team site without an office 365 group is created.

## Communication Site

Change the *SiteDesign* to something not equal to Team.

To enable *ShareByEmailEnabled* set the *SharingCapabilities* not equal to Disabled.

## Groups

To change the membership of the default built-in groups "\<sitename\> Visitors/Members/Owners" group, use \_Members, \_Visitors or \_Owners as group name.
