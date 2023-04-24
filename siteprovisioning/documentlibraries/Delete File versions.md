# Delete File versions

Use this format to delete minor or major versions, optionally based on Sharepoint Search Criteria. The filename should contain *DoclibDeleteFileVersion* and format is xls(x)

The following columns can be defined:

- ClientCode (optional)

- MatterCode

- Url

- Search (optional)

- MaxMinorVersions, number

- MaxMajorVersions, number

- DisableRecycleBin true/false

When a MatterCode is specified the doclib(s) from the matter are used. Specify an Url to specify a direct link to a document library

The *Search* property can contain a valid Sharepoint Search criterium. (or empty to return every file). The *Search* value is combined to a single search request to the server:

Size\>0 AND site:\"\<url\>\" AND (\<Search\>)

Example: Search = FileType:msg

Test the search criteria in sharepoint before starting the delete action using

Size\>0 AND Site:\"https://XXX.sharepoint.com/sites/123_003/Data/\" AND (FileType:msg)

If you want to remove minor versions, specify the maximum number of minor versions that should be available after the remove action. For example, 1 =\> only 1 minor version is left and all the other minor versions are removed (across other major versions), s0 0.1, 0.2, 1.0, 1.1 results in 1.0 and 1.1

If you want to remove major versions, specify the maximum number of major versions that should be available after the remove action. For example, 1 =\> only 1 major version is left and all the other major versions are removed.

By default the removed versions are moved to the recycle bin. Specify a true value in *DisableRecycleBin* to permanently delete the fileversions. Only supported in SPOnline, in 2013/2016 the versions is always permanently removed.
