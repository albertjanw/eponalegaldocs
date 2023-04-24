# AFAS

This pugin will periodically query the AFAS api rest web service for new and updated projects (matters).

Copy the dll files from the Plugins\AFAS directory to the site provisioning directory.  
Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the AFAS plugin.

Specify the **Url** and **AfasToken**.

## Jobs

Multiple jobs can be specified. Each job can use a different endpoint in Afas.

There are two types of jobs, the matter/project job and the documents job.
The matter/project job is used to fetch projects in AFAS and create the matter in Sharepoint.
The documents job is used to fetch documents from AFAS for a previously created matter in Sharepoint.

**DocumentJob**\
Set the property DocumentJob to true or false, so that you activate the document job or the matter/project job.

## Matter/Project Job

**DocumentJob**\
DocumentJob property must be set to false.

If the fieldnames in AFAS are unknown, leave the setting *LastRunDateTimeFieldName* empty and set *Debug* to true. The first 10 items will be exported and the json with all the fields are added to the log.

The following optional properties can be set:

**Debug**\
If enabled, the json result for each afas request is added to the log.

**Job Url**\
Set the url for the matter job. Matter url example: profitrestservices/connectors/SharePoint_Projecten

**LastRunDateTimeFieldName**\
Specify the fieldname from AFAS that contains the Last Modified value. This will be used to fetch changes. If this setting is empty only the first 10 items will be exported.

**Client Code**\
Json file property to match the sharepoint client code field, for example: Nummer. It's also possible to use dynamic properties. The property name should be available in the returned json, for example: CL_{Nummer}

**Client Name**\
Json file property to match the sharepoint client name field, for example: OrganisatieNaam. It's also possible to use dynamic properties. The property name should be available in the returned json, for example: CL_{Nummer}

**Client Field Mapping**\
Optional field that maps json file client properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null.
Leave empty for dynamic values config default
For example: Administration_name=Naam_administratie|otherproperty;EmptyTest=

**Matter Code**\
Json file property to match the sharepoint matter code field, for example: Project.

**Matter Name**\
Json file property to match the sharepoint matter name field, for example: Omschrijving.

**Matter Field Mapping**\
Optional field that maps json file matter properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
Leave empty for dynamic values config default
For example: Description=Omschrijving;Remarks_Project=Opmerkingen_Project;Actual_Date_Done=Werkelijke_datum_gereed|otherproperty

**Team Members**\
Optionally teammembers can be loaded for each project/matter.

*Url*, specify the endpoint that will return the members for a project/matter.\
*Filter ColumnName*, specify the columnname that will be used to filter for a specific project/matter.\
*Filter Value ColumnName in Source*, specify the columnname in the project/matter that will used as the filter value (contains unique project/matter id)\
*Emailaddress ColumnName*, specify the columnname that is used in the result to fetch the emailaddress of the member.
*Members column name in Result*, specify the columnname that is used in the result matter json.

The configuration will result in an url:\
```<url>?filterfieldids=<FilterColumnName>&filtervalues=<FilterValueColumnNameInSource>&operatortypes=2```

## Document Job

**DocumentJob**\
DocumentJob property must be set to true.

The job will fetch 3 different urls. First the document (info such as filename, id and project reference), second the file (binary data) and third the project metadata (extra info on project).

The following properties should be set:

**Debug**\
If enabled, the json result for each afas request is added to the log.

**Job Url**\
Set the url for the documents. Document url example: profitrestservices/connectors/Profit_Subject_Attachments_2

**LastRunDateTimeFieldName**\
Specify the fieldname from AFAS that contains the Last Modified value. This will be used to fetch changes. If this setting is empty only the first 10 items will be exported. For example: Instuurdatum

**Matter Code**\
Json document property to match the sharepoint matter code field. This property is used to open connection to Sharepoint Matter. for example: subject_id.

**Document:**
**Document ProjectID Column Name**\
Json document property to match the document project id field. This project id will be used to fetch metadata for the document. for example: subject_id.

**Document FileId ColumnName**\
Json document property to match the file id field. for example: file_id.

**Document FileName ColumnName**\
Json document property to match the file id field. for example: file_name.

**File:**
**FileUrl**\
Set the url for the files, to fetch files binary data. File url example: profitrestservices/fileconnector

**FileDataColumnName**\
Json file property to match the file data field. for example: filedata.

**Metadata:**
**DocumentMetadataUrl**\
Set the url for the metadata, to fetch extra info on project. File url example: profitrestservices/connectors/SharePoint_Dossiers

**DocumentMetadataFilterColumnName**\
This property is a filter to query the API. Specify which property has project id that should be filtered to fetch the metadata. for example: DossierId.

**DocumentMetadataMapping**\
Optional field that maps json file matter properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
Leave empty for dynamic values config default
For example: FileType=DossierType;Description=Omschrijving;FileId=DossierId;Date=Instuurdatum;Subject=Onderwerp;Explanation=Toelichting;Status=StatusNumber=Nummer;

**Sharepoint:**
**DocumentTargetFolder**\
This property is the Sharepoint matter target folder, where to store the files. For example: Documents
