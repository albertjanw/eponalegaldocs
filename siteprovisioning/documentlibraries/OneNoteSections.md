# OneNote Sections

Use this excel handler to import OneNote sections into existing doclibs.

- Matter/ClientCode
- Url
- SiteSet
- Section
- ....

If a *siteset* is specified the OneNote section files are loaded from the siteset.

If a *section* is specified, it's assumed to be a filepath to the \*.one files. Optionally use the syntax `<local filepath>=<sectionname>` to specify the sectionname that should be used in Sharepoint.

If a *mattercode* is specified, the siteurl from the matter is used to load the *SiteAssets* doclib and upload the onenote section(s) to the site notebook.

If no mattercode is specified, it's assumed the *Url* column contains a doclib url. The onenote sections will be added to the first notebook folder found in the rootfolder.
