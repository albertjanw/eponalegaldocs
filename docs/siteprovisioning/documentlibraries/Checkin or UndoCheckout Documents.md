# Checkin or UndoCheckout Documents

Use this format to checkin or undo checkout documents(s) in a document library. The filename should contain *CheckinDocuments* and format is xls(x)/csv.

The following columns are required:

- Url or MatterCode

- ClientCode (optional)

- Folder (optional)

- CheckinType, values are Minor, Major, Overwrite, default is Minor. (optional)

- UndoCheckout, true (optional)

- CheckedOutDays, (optional), number of checked out days (default 30)

The *Folder* contains the relative path to the existing folder in the doclib.

Only files that are checked out longer then *CheckedOutDays*, are handled. To disable this filter and check in all files, use 0 (days) or leave empty.

If UndoCheckout is true, the checkout status will be undone, resulting in possible data loss (current modifidations to the document are lost).
