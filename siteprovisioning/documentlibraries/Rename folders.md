# Rename folders

Use this format to rename folder(s) in a document library. The filename should contain *RenameFolder* and format is xls(x)/csv.

The following columns are required:

- Url or MatterCode

- Folder

- NewFolder

The *Folder* contains the relative path to the existing folder and the *NewFolder* contains the new name of the (deepest folder).

For example:

Folder = correspondence\\emails,\
NewFolder=\_emails

results in correspondence\\\_emails
