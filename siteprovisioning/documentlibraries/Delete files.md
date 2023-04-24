# Delete files

Use this format to remove files from a document library. The filename should contain *DeleteFile* and format is xls(x)/csv.

The following columns are supported:

- Url
- Force (optional)
- RecycleBin (optional)
- ClientCode (optional)
- MatterCode (optional)
- SiteUrl (optional)
- Modified (optional)

If Force is true and the file is checked out, an undo checkout command is executed before the file is deleted.

IF RecycleBin is true, the file is moved to the recylebin.

If Modified has a value, the file is only deleted/moved to the recyclebin if the last modified date of the file is equal (round to seconds) to the specified value. The specified time is converted into UTC using the timezone of the Web.

    For better performance specify a Client/Mattercode or a SiteUrl. This will group the files and remove the files  with a single connection for each Client/Mattercode or a SiteUrl
