# Sharepoint

- Url

Enter the complete url to the sharepoint site(collection) where the DMSforLegal Clients and Matters lists are located, for example: <https://demo.sharepoint.com>

- Relative Url

Specify the location where new site(collection)/doclibs are created.

Example 1: /sites\
In combination with the *Url* <https://demo.sharepoin.com/legal>, new items will be created in <https://demo.sharepoint.com/sites>

Example 2: sites (no prefix slash)\
In combination with the *Url* <https://demo.sharepoin.com/legal>, new items will be created in <https://demo.sharepoint.com/legal/sites>.

It's also possible to used dynamic names in the relative url. See 3.8.

For the client matter design *MatterSite* and *MatterDoclib* it's also supported to specify multiple url's (; or , separated). The new sites/doclibs are spread over the specified url's during provisioning.

## Authentication

### On-Premise

Specify the domain\\username and password for the connection. Leave empty to use the current windows credentials (in console mode) or the specified windows service account user.

### Sharepoint Online

Specify the username and password for the connection. Leave password empty to support weblogin (mfa) (only supported in console mode!!).

### Active Directory Application

Leave the username and password empty to use an AD application for authentication.

See <https://portal.eponalegal.com/projects/knowledge-base-site-provisioning/wiki/Azure_AD_Application_Registration_(application_permissions)>

For the specifc permissions see this [site](https://docs.microsoft.com/en-us/sharepoint/dev/sp-add-ins/add-in-permissions-in-sharepoint)

If authentication is failing using clientid / secret key, disable the DisableCustomAppAuthentication via
`set-spotenant -DisableCustomAppAuthentication $false`

### Azure AD App-Only via a Certificate

Generate a private certificate and upload the certificate and password to the new AD Application.

Install the PnP powershell module via ```Install-Module -Name PnP.PowerShell``

Create a new private certificate with a password:

```New-PnPAzureCertificate -CommonName "<name>" -OutPfx <name>.pfx -OutCert <name>.cer -CertificatePassword (ConvertTo-SecureString -String "<password>" -AsPlainText -Force)```

Upload the *.cer file to the application in the Azure portal

Specify in the Configurator:

- ClientId
- Certificate Path to the pfx file
- Specify the certificate password in the Application Secret Key

Assign the following permissions:

- Sharepoint, Sites/Termstore Full control
- MS Graph, Group/Team/Sites/Termstore, ReadWrite and User ReadAll

## AutoNumber ClientCode/MatterCode

Specify a value to enable autonumbering of clients and/or matters. This value will be used for the first empty client/mattercode. The next numbers are incremented with 1 and stored inside the \\Config\\Numbers directory. Each configuration contains its own auto-numbering file. The file can be changed using a text editor and will be automatically reloaded after a change. Only empty client/mattercode are filled with an autonumber (if autonumber is configured). It's possible to use other variables like {ClientCode}, see dynamic names.

Use *yyyy* or *yy* to use the current year.

Example (ClientCode=12345, next number = 12):

~~~text
yyyy-{ClientCode}.\#\#\#\# =\> 2017-12345.0012\
{ClientCode}.\# =\> 12345.12\
yy\#\#\# =\> 17012
~~~

The numbering is stored in \<install\>\\Config\\Numbers\\\<name\>.json. For each unique combination an entry is added to the file to preserve the highest number.

By default the numbering is restarted with the startnumber for each new combination (year or other variables). To disable the restart set the *ClientCodeNumberNoReset*/*MatterCodeNumberNoReset* to true. Be careful when activating this option after numbering has already started. Manually adjust the number json and make an entry for the *Client* and/or *Matter* with the new starting number.
