# Add entries MyMatters List

Use this format to add entries to the matter list. The filename should contain *MyMatters* and format is xls(x)

The following columns are required:

- ClientCode (optional)

- MatterCode

- User

- Title (optional)

- Category

- Remove

The *user* column should contain an usernames/email address. The folder for this user will be created if necessary.

If a *Title* is specified the this value is instead of the Title value from the Matter.

If a *Category* is specified a subfolder is created and the matter entry is added to the subfolder (will be created if necessary)

If *Remove* is *true* the item is removed from the my matters list for the specified user.
