# Reassign Group Set

Use this format to reassign the group / groupmembers in one or more site collections. The filename should contain *\et* and format is xls(x)

The following columns are required:

- Url

- Group

Optionally add more columns when variables are used inside the name / users / groups inside the groupset.

The url can contain a serverrelative sitecollection url (start with /) or use the url relative to the document library.

The group should contain the name of the groupset from the configuration.

It's also possible to create or update a group with members without specifying a groupset. Use the following columns:

- Url (siteollection url)

- GroupName

- GroupMembers

- GroupOwner (optional)

- GroupDescription (optional)

- GroupAllowMembersEditMembership (optional, yes/no)

- GroupOnlyAllowMembersViewMembership (optional, yes/no)

Specify the group members with an ; as separator.
