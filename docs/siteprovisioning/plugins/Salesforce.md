# Salesforce

This plugin will periodically query the Salesforce API for new and updated information. It will start a query with a filter based on the "modified on" date.

To connect the following information is necessary:

- ClientId
- ClientSecretKey
- UserName
- Password

## Query

Specify a query to fetch information. See the [salesforce documentation](https://developer.salesforce.com/docs/atlas.en-us.soql_sosl.meta/api/sforce_api_calls_soql_select.htm).

To test queries use the [Salesforce Workbench](https://workbench.developerforce.com/login.php)

*ObjectType*\
Specify the object that should be returned, for example: Lead, Case, Account

*Fields*\
Specify comma separated the required field from Salesforce, use FIELDS(STANDARD) to return the default fields. In *Test* mode this setting can be configured with FIELDS(ALL), but due to Salesforce limitation this can't be used in normal mode.

*Where*\
Specify the where statement for the query, for example:\
IsDeleted = false AND IsClosed = false

The plugin will modify the query and append the following:

AND LastModifiedDate > 2021-06-01T14:00:00Z

The datetime is the *LastRunDateTime* fetched from ./Config/Salesforce/*.json)

Sample queries:

~~~sql
SELECT Name, StageName, CloseDate, Amount, Owner.Name, Owner.Username FROM Opportunity 
WHERE (StageName = 'Closed Won' AND CloseDate = THIS_MONTH) AND OwnerId IN (select Id from user where UserRoleId = '00E0B000000zEGn')

SELECT FIELDS(ALL),Account.Name FROM Opportunity
~~~

## Test

If the setting Test is enabled, the fetched information from salesforce and the result client matter json is stored in the ./Monitor/Test directory. The LastRunDateTime is not updated!\
Use this mode to check the information returned from Salesforce and the result mapping.

## Mapping

Specify the fieldname from Salesforce and the target (internal) SharepointName.
Use the dot syntax to specify a nested value, for example *attributes.type* will return *Case*

~~~json
{
 "attributes": {
  "type": "Case",
  "url": "/services/data/v52.0/sobjects/Case/5001T00001SJKqdQAH"
 },
 "Id": "5001T00001SJKqdQAH",
 "IsDeleted": false,
 "MasterRecordId": null,
}
~~~
