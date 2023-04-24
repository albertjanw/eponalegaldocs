# Delete folders

Use this format to remove folder(s) from a document library. The filename should contain *DeleteFolder* and format is xls(x)/csv.

The following columns are required:

- Url or MatterCode

- Folder

- Force (optionally true/false)

- RecycleBin (optionally true/false)

If the folder contains items (subfolders or files), the folder is only removed if the *Force* column contains true.

If the specified *Folder* is empty all items (subfolders and files) in the doclib are removed (if *Force* is true)

If *RecycleBin* is true, the items are moved to the recycle bin and not really deleted.
