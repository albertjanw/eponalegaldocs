# Create Document libraries views

Use this format to create/update/remove views in a document library. The filename should contain *DoclibView* and format is xls(x)

The following columns are required:

- Url (optional)

- MatterCode (optional)

- MatterCode (optional)

- View

- Delete (optional)

If *Url* is empty, the *MatterCode* is required.

The *View* contains one or more names (; or , separated). The view name is used to load the configuration from the config file and the view settings are applied to the documentlibrary.

Specify a Boolean true value (1 or true) in the *Delete* column to remove a view from a doclib. It's not necessary that the view is defined in the configuration.

Optionally add more columns when variables are used inside the name / users / groups inside the view.
