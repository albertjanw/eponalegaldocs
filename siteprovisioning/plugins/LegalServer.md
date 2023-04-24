# LegalServer

Use this plugin to connect the site provisioning service to the LegalServer time and billing application (see <https://denovo.io/> ). Configure an url, username, password, apikey and reportnumber and map the legalserver fields to a sharepoint column. The api will export a report from legalserver. See <http://help.legalserver.org/home/reports/reports-api>.

To manually test the export start a http get with the username/password as basic authentication:\

~~~text
curl -u \"\<user\>\":\"\<password\" \"https://\<url\> /modules/report/api_export.php?load=\<reportnumber\>&api_key=\<apikey\>\" -i
~~~

*TestMapping*\
if enabled, don't export the json to the monitor directory, but export the json to the \<monitor\>\\Test directory. Use this option to configure/verify the mapping.

*ExportMatterForCaseDispositionValues\
*By default all matters are exported to Sharepoint. Specify one or more case disposition values to export the matter for these values. Possible values:\

- Open
- Closed
- Pending
- Prescreen
- Rejected
- Incomplete Intake

*MapClientCode/Name*\
Configure a default clientcode and clientname for matters that don't have a client (yet) in LegalServer or specify the fields that contain the client code and name (by default Client_ID and Full_Name\_\_Last\_\_First\_).

*MapMatterCode/Name*\
By default the field Matter_Case_ID\_ is mapped on the mattercode. There's no matter name field in LegalServer. Optionally configure a dynamic mattername in the site provisioning based on other values.

*MapMatterFields*\
Specify other fields in the format of:\
\<legalserverfield\>=\<sharepointcolumn\>;\<legalserverfield\>=\<sharepointcolumn\>

*CheckForChangesCacheInDays*\
The report will always export the new/changed matters since X days (configured in the report). The lastrundatetime from Site provisioning is not used. This can result in many updates during the day of the same matter. When a matter is exported to Sharepoint the site prov. service caches the result for this matter. Specify the number of days that matter should be hold the cache. After a restart of the site prov. service, the cache is empty and all matters are exported again.

Sample Export:

~~~xml
<row\>
<Database_ID\>370101\</Database_ID\>
<Full_Name\_\_Last\_\_First\_\>Wise, Tonisha\</Full_Name\_\_Last\_\_First\_\>
<Primary_Advocate\>Intake, Client\</Primary_Advocate\>
<Date_of_Latest\_\_Opened\_\_Intake\_\_Prescreen\_\>2020-09-02T00:00:00-00:00\</Date_of_Latest\_\_Opened\_\_Intake\_\_Prescreen\_\>
<Epona_Documents\>t\</Epona_Documents\>
<Epona_Documents_Date\>2020-09-02T00:00:00-00:00\</Epona_Documents_Date\>
<Intake_Date\>2020-09-02T00:00:00-00:00\</Intake_Date\>
<Matter_Case_ID\_\>20-0370101\</Matter_Case_ID\_\>
<First_Name\>Tonisha\</First_Name\>
<Last_Name\>Wise\</Last_Name\>
<Case_Disposition\>Pending\</Case_Disposition\>
<Case_Status\>Intake Queue\</Case_Status\>
<Intake_Program\>Client Intake Workgroup\</Intake_Program\>
<Initial_Legal_Problem_Category\>Housing\</Initial_Legal_Problem_Category\>
<Legal_Problem_Code\>\</Legal_Problem_Code\>
<Client_ID\>249051\</Client_ID\>
</row\>
~~~
