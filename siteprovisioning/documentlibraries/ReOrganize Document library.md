# ReOrganize Document library

Use this format to reorganize *all* folders in a document library. The filename should contain *DoclibReOrganize* and format is xls(x)/csv. Use this import to split (large) folders into multiple folders based on the DMSMessageDeliveryTime or LastModified. Each document in the folder is moved into a \_\_\<year\>\\\<month\> folder.

The following columns are required:

- Url or MatterCode (/ClientCode)

- FileExtension (optional)

If an extension is specified (like msg) only files with the specified extension are moved.
