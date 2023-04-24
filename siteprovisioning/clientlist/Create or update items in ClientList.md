# Create or update items in ClientList

Use this format to create/update items in the client list. The filename should contain *ClientList* and format is xls(x)

The following columns can be defined:

- ClientCode (required)

- ClientName

- ... additional columns are mapped on the client list column names

If ClientName is not specified the clientname and title are not updated.

To update the ClientCode with a new value, specify the original value in the ClientCode column and add a column with the name *\_\_Code\_\_* and the new ClientCode.
