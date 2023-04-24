# Plugins

Copy the necessary files from the .\Plugin directory to enable these jobs.

## Sync Sharepoint Groups

Use this job/plugin to periodically sync members of a sharepoint group from a 'template' site collection to the other site collections. The group should exist in the other sitecollections, missing groups are not created and skipped.

The group will only be synced from the source to the other sitecollections when the source group is changed. The last state of the group is stored in the \Config\SyncSharepointGroups file.

Create one master site collection where the membership of all the sharepoint groups is maintained. Periodically the job scans the master site collection for changes. To identify if the sharepoint group is modified an unique hash is stored in the \\Config\\SyncSharepointGroups for each group. When the hash is not changed, the group is not synced to the other sitecollections.

The sitecollections that are updated can be configured via:

- SiteCollectionUrls\
if one or more urls are specified only these sitecollections are updated.
- UseSharepointRootServerRelativeUrlForSiteCollections\
if true only the url's specified in the SharepointRootServerRelativeUrl are updated.
- Else\
Every sitecollection from the matterlist is updated (if not specified in the ExcludeSiteCollectionUrls)

Configuration:

- TemplateUrl\
The master sitecollection where the groups are maintained

- ExcludeSiteCollectionUrls\
Optionally specify one or more urls that should be skipped

- Groups\
Leave empty to sync all the sharepoint groups (not recommended, due to default groups) or specify the names of the groups that should be synced

To manually start the job create a (text)file with the name *SyncSharepointGroup* and put that file in the monitor directory of the service. The job will be started instantly.

During site creation / updates the template group can also be specified using the *Url* property of the Group configuration.
