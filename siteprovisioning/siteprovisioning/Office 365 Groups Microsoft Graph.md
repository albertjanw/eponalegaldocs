# Office 365 Groups / Microsoft Graph

When the site provisioning should create Office 365, the MS Graph API is used and should be properly configured.

Goto <https://portal.azure.com>

Select Azure Active Directory Services

Select App registrations

- Create a new application

- WebAPI / API

- Create App

- Copy ClientID / Toepassings ID (Application ID) and add this key to Site prov. Configuration SharepointClientID

Permissions

- Add MS Graph

- Add all Application Permissions OR Group.ReadWrite.All, Site.ReadWrite.All, User.Read.All, Notes.Read.All

- !! Click on *Grant Permissions* before authenticating the first time !!

Keys

- Generate a new Key

- Copy Key and add this key to the Site Prov Service SharepointClientAppKey

<https://apps.dev.microsoft.com/>

or

<https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps>

Create another application to support access via an user token (require for some updates, like updating logo and the beta msgraph)

- Create a new application

- Native

- Create App

- Copy ClientID / Toepassings ID (Application ID) and add this key to Site prov. Configuration *Client ID Delegated User*

- Add Permissions

- Add MS Graph

- Add

  - all Application Permissions\
  
    OR

  - Group.ReadWrite.All, Directory.ReadWrite.All.

- !! Click on *Grant Permissions* before authenticating the first time !!
