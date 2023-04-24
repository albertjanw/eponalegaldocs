# Import documents from template

Use this format to import documents from a template folder in an existing document library. The filename should contain *DoclibImportDocumentsFromTemplate* and format is xls(x)

The following columns are required:

- Url or MatterCode (optional)

- DoclibSet

- SourceFolderUrl (optional)

If *Url* is empty, the *MatterCode* is required. The Url should point to an existing doclib.

The *DoclibSet* contains the name of the doclibset.

If *SourceFolderUrl* is empty, the *SourceFolderUrl* is used from the doclib set. The Url should point to an existing folder that contains the documents that should be copied to the document library.

Optionally add more columns when variables are used inside the folders / settings in the doclibset.
