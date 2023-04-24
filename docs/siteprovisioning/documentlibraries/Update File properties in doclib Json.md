# Update File properties in doclib (Json)

Use this format to update the properties in a doclibs. The filename should contain *UpdateDoclibFileProperties* and format is json. To be backwards compatible with the server version, the filename can also be *AssignDefaultValuesInDocLib\*.json*.

The json document should be a dictionary with key and value. The MatterCode or Url is required. The other specified properties are assigned to all the documents in the doclib.

Use the propertyname *__DoclibUrl* to specify an url to a doclib.

Due to technical reasons on Sharepoint On-Premise the version settings are temporarily disabled during updating the metadate, to prevent new versions of the document.
