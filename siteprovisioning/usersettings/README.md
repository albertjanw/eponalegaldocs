# Create or remove entries in the My Favorites in User Setting List

Use this format to create or remove favorites in the User Setting List.

The following columns can be used:

- UserName

- ClientCode

- MatterCode

- Title (optional)

- Url (optional)

- SiteUrl (optional)

- TargetFolder (optional)

- Remove

The entry will be added for the user specified in *UserName*.

If no Title is specified the title from the matter from matterlist is used combined with the last part of the url / targetfolder.

If a MatterCode is specified, the Url and SiteUrl are fetched from the matterlist. The targetfolder is appended to the Url (if specified).

If no MatterCode is specified the Title, Url and SiteUrl are used to create or remove a Favorite item.
