# Microsoft Dynamics

This plugin will periodically query the Microsoft dynamics API for new and updated matters. It will query for *incidents* with a filter based on the "modified on" date.

Create a ClientID and SecretKey There are no additional permissions required. See <https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/authenticate-oauth#use-client-secrets--certificates>

Specify the Tenant url without https:// (for example epona.onmicrosoft.com). This is used to login into the tenant using the url [https://login.microsoftonline.com/{tenant}](https://login.microsoftonline.com/%7btenant%7d).

The ClientID should be associated with an application user that is defined in Microsoft Dynamics. See <https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/authenticate-oauth#connect-as-an-app>

Add the securityrole/permissions to the new user.

It's possible to define a filter on what matters are imported based on the MatterCode (for example "PRJ\_\*" to only import mattercode that start with PRJ\_).

Use a LastRunDateTime date before 1-Jan-2000 to fetch all matters.
