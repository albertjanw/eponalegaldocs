# Report OneNote

Use this excel handler to make a report of the onenotes/noteboks that are currently stored in Sharepoint. The filename should contain *ReportOneNote* and format is xls(x). The result file will be named *inputfilename*_result.xlsx and stored in the same directory as the source file.

- MatterCode\
Specify the MatterCode (and clientcode if not unique).\
The document library from the matterslist for that matter will be queried for onenote files and dumped. Also the SiteAssets doclib in the site will be queried als also dumped.

or

- Url\
Specify the full url to the document library. Only this library will be queried for onenote files.

The result file will contain the following columns:

- SiteUrl
- DoclibUrl
- NotebookUrl
- IsEmpty
- Modified
- ModifiedBy
- Created
- CreatedBy
- Error
