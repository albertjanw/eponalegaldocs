# Update Default values in doclib

Use this format to update the properties in the linked doclibs. The filename should contain *UpdateDoclibFileProperties* and format is excel.

The following columns can be defined:

- ClientCode

- MatterCode (required)

- ... additional columns are mapped on the list column names

The MatterCode is required. The other specified properties are assigned to all the documents in the doclib linked to the matter.

Due to technical reasons on Sharepoint On-Premise the version settings are temporarily disabled during updating the metadate, to prevent new versions of the document.
