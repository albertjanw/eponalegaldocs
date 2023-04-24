# Site sets

## Template

The site prov. tries to find match on the existing templates on the template Title or ends with \#\<template\>on the Name. If not found, it will upload the file to the catalog from disk, make sure the filename of the template and title are equal.

## Template Configuration

- QuickNavigation

When Remove is true, an existing navigation item is removed based on a match on the *Title.*

## Doc ID provider

The *Code* specified for the site collection is also used for the doc id prefix. Special characters are removed, only letters and numbers are supported. The minimum length is 4 characters, zeros are prefixed if the length is too short. The maximum length is 14 characters, the last 14 characters are used when the length is too long.

## Matter Status Open / Closed

The matterlist can contain a column that holds the matterstatus. This column can be configured in the *Settings, SiteProvisioning, MatterStatusColumnName*. Together with the option *MatterStatusClosedValues* a site can have a status of Close or Open.

Via an EXISTING policy that is created in the sitecollection, a policy can be applied when the matter status is closed. For example to make the site readonly.

A policy can be created manually in the sitecollection or published via the contenttype hub. Before a policy can be applied it should be active on the site. The name of the policy (case sensitive!!) can be configured on the web set, *PolicyName*.

## Site sharing

To change the site sharing change the setting RequestAccessEmail to true or false. If enabled optionally specify an emailaddress in the setting RequestAccessEmailAddress. If the email adress is empty and *RequestAccessEmail* is enabled,the default "owners" group is set.

## OneNote Sections

When a new site/sitecollection is created one or more sections can be automatically deployed to the new site notebook. Export the notepage page to a local \*.one file. Specify the file(s) in the *OneNoteSections* setting in the SiteCfg. It's possible to use dynamic properties. Examples (filepaths can be relative (to the siteprov directory) or absolute)":

- onenote/{department}/Default.one
- onenote/{department}   (extension will be automatically added)

By default the section name in Sharepoint is equal to the local filename. To override the section name in sharepoint, use the following syntax:  `<local filepath>=<sectionname>`
