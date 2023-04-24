# Configure CDN

Use PnP Powershell

- Connect

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

- Check if CDN is enabled

```powershell
Get-PnPTenantCdnEnabled -CdnType Public
```

- If not enabled, enable without the defaults:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true -NoDefaultOrigins
```

- Create a new doclib CDN and add the files.

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl CDN
```

- Test if the CDN is available, can take max 15 minutes (will return configuration pending if not yet ready)

```powershell
Get-PnPTenantCdnOrigin -CdnType Public
```
