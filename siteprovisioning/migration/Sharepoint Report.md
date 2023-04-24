# Sharepoint Report

Use the tab *Export* and the button *Report* to create a report on folders found in Sharepoint. For each matter from the matterlist the folders are fetched and the filecount for each folder is stored. This information is exported to excel and stored in the database in the table *_EDMSSharepointFolder*.

This export can be used to make a match with the source to validate or report the migration result.

If no mattercodes are specified, all matters from the matters list are exported, else only the specified mattercodes.

For each mattercode, the current information stored in the database for that specific matter is removed and the new items are added.

The following information is stored in excel and the database:

- MatterCode
- DoclibUrl
- Folder
- FileCount
