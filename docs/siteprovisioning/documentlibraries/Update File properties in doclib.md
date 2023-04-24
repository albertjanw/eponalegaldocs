# Update File properties in doclib

Use this format to update the file properties in doclibs. The filename should contain *UpdateDoclibFileProperties* and format is excel.

The following columns can be defined:

- ClientCode (optional)
- MatterCode
- Url
- ... additional columns are mapped on the list column names

The MatterCode or Url is required. The Url should point to the root of a doclib. The other specified properties are assigned to all the documents in the doclib linked to the matter.

Due to technical reasons on Sharepoint On-Premise the version settings are temporarily disabled during updating the metadate, to prevent new versions of the document.
