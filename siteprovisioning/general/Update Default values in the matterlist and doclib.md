# Update Default values in the matterlist and doclib

Use this format to update the matterlist and the default values in the linked doclibs. The filename should contain *defaultvalues* and format is xls(x)/csv.

The item in the matterlist will be updated and the default values in the linked doclibs are updated. **Optionally** all the documents in the doclib can also be updated (resulting in incrementing the minor version of the document).

Only values from the excel sheets are used to update the default values (not from the existing matterlist item)

The following columns can be defined:

- ClientCode

- MatterCode (required)

- MatterName (required)

- UpdateDocuments, if set to TRUE / 1 / Y all the metadata in the documents are also updated.

- ... additional columns are mapped on the list column names
