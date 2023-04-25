# Create FolderSets

Use this format to create folders in a document library. The filename should contain *FolderSet* and format is xls(x)

The following columns are required:

- Url (optional)

- MatterCode (optional)

- MatterCode (optional)

- Folder

- FolderSet

If *Url* is empty, the *MatterCode* is required.

The *FolderSet* contains one or more names (; or , separated). The folderset name is used to load the configuration from the config file and the configured folders in the folderset are created in the documentlibrary.

The *Folder* column can be used to specify one or more folderpaths (; or , separated). The specified folderpaths are created in the documentlibrary.

Optionally add more columns when variables are used inside the name / users / groups inside the view.
