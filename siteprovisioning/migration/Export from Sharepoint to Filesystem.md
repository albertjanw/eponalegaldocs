# Export from Sharepoint to Filesystem

Use the tab *Export* to export files from Sharepoint to the filesystem.

- Specify one or more matternumbers (splitted by ; or , or line)\
Use \| as separate for clientcode\|mattercode format (when
mattercode is not unique)

> OR

- Specify one or more Urls (splitted by new line). The url should be a valid site or doclib. Optionally specify the mattercode/name of the
export directory using the syntax:\
url=exportfolder\
Every doclib found is exported to the filesystem.\
Enable the option 'export subsites' to recursively export all doclibs in all sites beneath the supplied url.

Specify an export directory. For each matter a subdirectory will be created.

Optionally compress each matter into a zip file (and remove the compressed files from the filesystem).

Optionally create empty directories on the filesystem. If not enabled, empty directories are skipped and not created.

Optionally export all versions of the documents. The file name notation is \<name\>\_\_v\<version\>\<extension\>.

If the export is restarted a delta export is started. The LastChange date of the doclib/folder is compared to the local Lastwrite stamp of
the directory. If the doclib last change date is newer all files are fetched and only new of changed files are exported. When the export of
the doclib/folder is finished the local last write timestamp of the folder is updated with the last changed date form the doclib/folder in
sharepoint.
