# Installation of Epona Matter Center SPFX

Epona MC SPFX is a SharePoint hosted app following the modern Office365 SPFX technique. Like all Office SPFX apps, it resides in a SharePoint app catalog. When published, Epona MC SPFX can be added to any SharePoint page in the DMSForLegal site collection.

Like other parts of DMSforLegal the configuration settings are stored in the DMS Configuration list. However, for the default layout, no extra settings are needed in DMS Configuration.

## App catalog

An app catalog should only be created once in an SharePoint environment. For an existing tentant, this might already be there, otherwise it should be installed using the SP admin interface.

1- Open the \&lt;domain\&gt;-admin.sharepoint.com, navigate to &#39;More features&#39; and open &#39;Apps&#39;

 ![](./img1.png)

2- Select &#39;App catalog&#39;

 ![](./img2.png)

3- Leave &#39;Create a new app catalog site&#39; selected and click &#39;OK&#39;

 ![](./img3.png)

4- Fill in the form. The name &#39;apps&#39; for the catalog is most often used. After submitting the form the apps catalog will be created. This can take several minutes.

 ![](./img4.png)

5- After submitting the form the apps catalog will be created. This can take several minutes.

## SiteCollection App Catalog Installation

Follow these steps to install the EponaDMS365 webpart solution in a single sitecollection. Site collection admin permissions are required. The tenant wide webpart version is ignored (if installed)

> This option can also be used to test a new version.

The target sitecollection should be configured as an 'App Catalog' sitecollection using the following powershell

```Powershell
Connect-SPOService -Url https://<tenant>-admin.sharepoint.com
# create site collection app catalog
Add-SPOSiteCollectionAppCatalog -Site https://<tenant>.sharepoint.com/sites/epona
```

For more information see [docs.microsoft.com](https://docs.microsoft.com/en-us/sharepoint/dev/general-development/site-collection-app-catalog)

When the app catalog is enabled in the sitecollection:

- browse to the url `https://tenant.sharepoint.com/sites/epona/appcatalog`
- install/deploy the webpart, see [Tenant installation](#tenant-app-catalog-installation)

## Install or update the SPFX app

The latest package file can be retrieved from [Documentation for Epona products](../readme.md).

1- Get a local copy of epona-dms-legal.sppkg.
2- Navigate to the app catalog site and select &#39;Distribute apps for SharePoint&#39;

 ![](./img5.png)

3- Either select &#39;Upload&#39;, or just drag the .sppkg fileto this page

 ![](./img6.png)

4- Select &#39;Make this solution available to all sites in the organization&#39; and click &#39;Deploy&#39; (You can choose not to check this box, but use the Settings, Add an app on the DMSforLegal site collection to make the app available )

 ![](./img7.png)

5- The app is now available for users to be added to a SharePoint page.

## Default installation on SharePoint page

1- Navigate to the Site Pages folder of the DMSforLegal site collection, and select &#39;New&#39;, &#39;Site Page&#39;

 ![](./img8.png)

2- Give the page the name &#39;MC&#39;, and click &#39;+&#39; to add a webpart. When typing &#39;ep&#39;, the &#39;Epona Dashboard&#39;

 ![](./img9.png)

3- Select the &#39;Epona Dashboard&#39; app, and publish the page. The app will become visible, including matters, my maters etc., if present.

 ![](./img10.png)

4- Settings can be changed using the DMS Configuration List. Special attention should be given to the Matters and Clients AddFields and EditFields settings for the &#39;Code&#39; field. These should be either set to &#39;View&#39; or &#39;Hidden&#39; if the value is provided by another process, for example by the Provisioning service.

 ![](./img11.png)

5- A few other settings can be configured using DMS Configuration Center

 ![](./img12.png)

## Sharepoint Fullpage App

Use the following link to load Epona DMS365 in a full page.

/_layouts/15/apppagehost.aspx?componentId=65a87007-ac17-41b6-ace1-b1755acd42f3

It's also possible to create a new modern page and add the *EponaDMS365* webpart to the page. Save the page with a name.

User PnP.Powershell to update the layout of the page to a single webpart page.

```powershell
Connect-PnPOnline -Url https://contoso.sharepoint.com/sites/epona
Set-PnPPage -Identity "<pagename>" -LayoutType SingleWebPartAppPage
```

## Contract feature

The contract feature extension for Epona MC SPFx can now be installed using the DMS Configuration tool. Once the feature has been enabled using the settings, a new option appears that allows it to install in EponaMC SPFx and be available from the menu.

It adds some settings to the DMS Configuration List (SPF category), that can of couse be changed manually afterwards.

![](./img13.png)

## Configuration

Configration can be done both by changing or adding listitems in the DMS Configuraion list manually, as well by installing in MCAdmin app.

See for instructions the EponaMC_configuration page from [Documentation for Epona products](../readme.md)\
