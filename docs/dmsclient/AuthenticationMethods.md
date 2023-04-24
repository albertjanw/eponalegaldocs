# Authentication Methods

> Authentication (Listed in Order of Preference)

## Modern Authentication

> This is the new, recommended method for authentication.

It requires an Azure Application Registration (Please refer to the document [Enable Modern Authentication in DMSforXXX](./EnableModernAuthentication.md).
This new method utilizes Microsoft's best practics for authentication and security using the 'Microsoft Authentication Library' (MSAL).
Once the application is properly registered, the following information will be required:

* Applications ID
* Username (UPN) (Email address for user.)

## Browser Authentication

> This authentication method can be used when Modern Authentication is not available.

Browser authentication is required when multi-factor authentication (MFA) is enabled for users.  
There is no requirement for the Username and Password to be entered.
Authentication will occur after Apply or OK is clicked.

A separate window will open where the user will login to Office 365 with their username and password.
This action will store an authentication cookie from Office 365.

**Users will be prompted to login again when their password changes, or the authentication cookie expires.**

## Other authentication

### Windows Authentication

> (Typically used for on-premises SharePoint environments.)

### Username and Password

> (Typically used for on-premises SharePoint environments.  Legacy/Basic Authentication)

### Multi-factor Authentication

> (Sometimes required for external multi-factor authentication protocols when Modern Authentication is not feasible.)
