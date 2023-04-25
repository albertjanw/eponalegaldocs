# Add or Remove O365 Group members or owners

Use this format to add or remove owners or members from an existing Office 365 Group. It's not a merge action, but always an add or a remove. The filename should contain *o365groupmember* and format is xls(x)/csv.

Use a ; to optionally specify multiple users in a single column.

The following columns can be used:

- MatterCode

- OwnerAdd

- OwnerRemove

- MemberAdd

- MemberRemove

If the member or owner already exists, the user is skipped when adding

If the member or owner is removed and not already a member of owner, the user is skipped.
