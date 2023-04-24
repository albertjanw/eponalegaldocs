# Update File properties

Use this format to update the properties of documents without changing the version/modified information. The filename should contain *updatefileproperties* and format is xls(x)/csv.

The following columns can be defined:

- ClientCode

- MatterCode

- Url

- SourceFile

- ... additional columns are mapped on document fields

Specify a clientcode/mattercode to fetch the document library url. In this case the SourceFile can contain a relative path from the root of the document library.

If no clientcode/mattercode is specified, the url column can contain a value for the site or documentlibrary url. In this case the SourceFile can contain a relative path from specified url.

For each unique combination of clientcode/mattercode/url a thread is started with a separate sharepoint connection. To speed up the process it's adviced to specify a mattercode or url.

The other columns that are specified are used to update the fields for the document specified in the SourceFile.

Due to technical reasons on Sharepoint On-Premise the version settings are temporarily disabled during updating the metadate, to prevent new versions of the document.
