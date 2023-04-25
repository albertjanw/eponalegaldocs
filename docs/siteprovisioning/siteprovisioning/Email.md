# Email

There are two options to get an email alert when an error has occurred:

## Send email during file processing

This method will only send a single email when the processing of a file has failed when dropped in the monitor directory. Configure the email settings in \\Settings\\Email.

## Send email via MS Graph

Microsoft has disabled basic authentication for Office 365 SMTP access. Enable the *Use MsGraph* setting to send emails via Ms Graph. Add the required **Mail.Send** permission to the app and give an admin consent.

It's strongly suggested to add an access policy to disallow sending email using every emailaddress that is allowed in the tenant. See <https://docs.microsoft.com/en-us/graph/auth-limit-mailbox-access>

## NLog Target error

Optionally you configure the service to send an email when an error has occurred somewhere in the application. You can specify the options in the Epona.ProvisioningService.exe.nlog file, see target *mailbuffer* and enable the rule *writeto=mail*. For all options see <https://github.com/nlog/NLog/wiki/Mail-target>

## Send email when matter is provisioned

If email settings are configured in \\Settings\\Email, users can optionally get an email when a new matter is created/updated and ready to use.

To enable this feature specify the settings in \\Settings\\Email\\ClientMatter

- NewMatter\
If enabled users will get an email when a new matter is created, else users will also get an email when the matter is updated.
- EmailAddressFrom\
Specify the from emailaddress. If left empty, the from emailaddress from the email settings is used
- EmailAddressTo\
Specify one or more emailaddresses (splitted by , or ; ). Optionally use dynamic fields like {Author}, {Responsible}, etc.
- EmailAddressCc\
Specify one or more emailaddresses (splitted by , or ; ). Optionally use dynamic fields like {Author}, {Responsible}, etc.
- Subject\
Specify the subject. optionally use dynamic fields like {MatterCode}, {MatterName}, etc.
- BodyFileName\
Specify the filename that contains the html body of the email. If no path is specified, the file should be stored in .\\ClientMatterEmail\\ subdirectory. Optionally use dynamic fields like {MatterType}, etc. to specify the filename.

### Email body text

The HTML body text from the email is read from the file. If the file is not found, the default file Matter.html (or NewMatter.html for a new matter) is used.

Don't use css inside an email html template. Use the online tool [https://htmlemail.io/inline/](https://htmlemail.io/inline/) to convert the html from css to inline styles. See _NewMatter.sample_css.html.

The HTML can contain dynamic fields (with double accolades!) and also dynamic text. For syntax reference see <https://sharpscript.net/>. See [Pagesets](../../siteprovisioning/siteprovisioning/Page%20sets.md#Text-webpart)

The following variables can also be used (use {{variable}} syntax )

- URL, url to the document library
- SiteURL, url to the sharepoint site
- Epona365URL, url to the Epona 365 page for the new matter.
