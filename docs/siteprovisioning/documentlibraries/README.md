# Add ContentTypes

Use this format to add content type(s) to a document library. The filename should contain *DoclibContentType* and format is xls(x)/csv.

The following columns are required:

- Url or MatterCode

- ContentTypes

- RemoveIfNotSpecified (optional)

Specify the name of the content types, use a ; or , as a separator.

If RemoveIfNotSpecified is true, existing contenttypes that are linked with the doclib and not specified in *ContentTypes* are removed.
