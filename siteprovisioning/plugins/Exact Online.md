# Exact Online

To access the REST API an Access token is required.

First create an application in Exact Online and get the ClientID and ClientSecret for this application. Use a redirect uri, <https://oauth2.eponalegal.com/>

See <https://support.exactonline.com/community/s/knowledge-base#All-All-DNO-Process-appcenter-eol-appcenter-dev-registerapp-p>

Use this url to get an Access token:

- Start a browser

- Open the url: [https://start.exactonline.nl/api/oauth2/auth?client_id=\<clientid\>&redirect_uri=https:%2F%2Foauth2.eponalegal.com%2F&response_type=code](https://start.exactonline.nl/api/oauth2/auth?client_id=%3cclientid%3e&redirect_uri=https:%2F%2Foauth2.eponalegal.com%2F&response_type=code)

(replace \<clientid\> with the correct client id from the newly created application

- Login with your exact online credentials and give the application you just created access

- The browser is redirected to an url like this: <https://oauth2.eponalegal.com/?code=XXXXX>

- Copy the value from the after ?code= and add this to the configuration Exact online using the configuration key "AccessCode"

Start the provisioning service within 3 minutes or else the access code is not valid anymore.

When a new authorization code is generated always remove the cached file in the \\Config\\ExactOnline\\\<currentsharepointconfig\>.json.

It's possible to define a filter on what matters are imported based on the MatterCode (for example "PRJ\_\*" to only import mattercode that start with PRJ\_).

## Mapping

See all fields on the [API Documentation](https://start.exactonline.nl/docs/HlpRestAPIResourcesDetails.aspx?name=ProjectProjects).

- MatterCode = Division.Prefix + Code
- MatterName = Description
- ClientCode = AccountCode
- ClientName = AccountName
- OriginatingUser = CreatorFullName
- SupervisingUser = ManagerFullName
- Classification = ClassificationDescription
- Division = DivisionName
- Type = TypeDescription
- MatterStatus = EndDate -> Archived/Open
- StartDate = StartDate
- EndDate = EndDate
