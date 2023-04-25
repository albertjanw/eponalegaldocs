# Set policy Matter Status

Use this format to set a policy and/or open or close a site. The filename should contain *MatterStatus* and format is xls(x)/csv.

The following columns are required:

- Url or MatterCode (/ClientCode)

- Policy

- MatterStatus (the only valid values are Open or Close)

If the Policy column is empty, the current applied policy is applied when the site is closed. Specify the policyname (case sensitive!!) to specify an EXISTING policy for the site. The policy should be manually created and/or published via contenttype hub.

If the MatterStatus is equal to Close, the site is closed and the policy is applied.\
If the MatterStatus is equal to Open, the site is (re)opened.
