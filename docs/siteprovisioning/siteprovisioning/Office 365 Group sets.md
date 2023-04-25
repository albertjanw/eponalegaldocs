# Office 365 Group sets

Use the *LogoLocalFilePath* setting to upload a logo. Variables are supported. The SiteLogoUrl from the attached site configuration will not work with a group.

## Members / Owners

The members and owners can also be configured to use a variable. At run time the members/owners are parsed and added.

The matterlist column can contain a multi-user column "Owners". Use the variable {Owners} in the office 365 group configuration in the *Owners* field.

Optionally the owners/members can also be updated, resulting in adding/removing owners/members from an existing O365 group. Enable *OwnerUpdate* or *MemberUpdate* to enable this.

Optionally the matter can also be added/removed for members/owners when the member/owner is added/removed to/from the group. Use *MemberAddMatterToMyMattersList* or *OwnerAddMatterToMyMatterList* to enable this. Use a ; as a separator for multiple values!

## Teams Channel / Tabs

One or more channels can be created inside the Team. Existing channels are matched on the displayname and if not found a new channel is created. The localized name for *General* is translated from other languages like dutch (Algemeen).

*Private  Channels*\
For private channels Sharepoint will create a new sitecollection. This sitecollection will be automatically provisioned with the configured site and pageset. It will check if the channel has a siteset configured and if not, the TeamChannelSiteSet on the Office365Group set or else the Office365group set.
Manual created private channels are provisioned with the TeamChannelSiteSet on the Office365Group set or else the Office365group set.

One or more MS Teams tabs can be configured for each channel.

Existing tabs are matched on the teamApp ID and if multiple found, also on the displayName. If not found a new tab is added.

Tabs are only deleted if *Remove* is set to true, for example to delete the default Wiki tab.

*SharepointPages* / *Sharepoint*\
If no url is specified, the home page is configured or specify a relative url to the page or list.

*SharepointNews*\
Show the news items from the current site/group. Url can be left empty.

*OneNote*\
The default OneNote linked to the site is fetched and configured for the tab. Url can be left empty

**Notes.Read.All** MS Graph Permissions are required!

*Planner*\
The tab is added, but not yet configured due to MSGraph delegated permissions requirement to read plans/tasks
