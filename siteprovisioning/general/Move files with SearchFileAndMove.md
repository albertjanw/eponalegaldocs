# Move files with SearchFileAndMove

Use this format to move one or more files based on Sharepoint Search Criteria. The filename should contain *SearchFile* and *Move* and format is xls(x)

The following columns can be defined:

- SourceFolder

- SourceFolderSearch

- TargetFolder

- RemoveEmptyFolder

In SP2013/2016 it's not possible to move a file to a different doclib/site/sitecollection, Export, import and delete the file is currently necessary. In SP Online the file can be moved to a different doclib/site/sitecollection.

The SourceFolder should contain the relatieve URL to the doclib or folder.

The SourceFolderSearch property should contain a valid Sharepoint Search criterium. (or empty to return every file). The SourceFolderSearch value is combined to a single search request to the server:

Size\>0 AND site:\"\<url\>\" AND (\<SourceFolderSearch\>)

Example: SourceFolderSearch = LastModifiedTime\<2020-06-23

Test the search criteria in sharepoint before starting the move action using

Size\>0 AND Site:\"https://XXX.sharepoint.com/sites/123_003/Data/\" AND (LastModifiedTime\<2020-06-23)

The files that are returned from the search are moved to the *TargetFolder* (relative url to a doclib or subfolder). The folderstructure from the source is recreated in the *TargetFolder* if necessary.

If *RemoveEmptyFolder* is true, at the end all empty directories (from the files that are moved) are deleted.

Large files (\>50mb) are first downloaded to a local file, uploaded to the targetlocation and moved to the recycle bin. ! Only the latest version is moved, previous versions are not moved, but are preserved in the recycle bin !
