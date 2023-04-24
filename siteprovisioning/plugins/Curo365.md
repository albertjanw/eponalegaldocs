# Curo365

Use this plugin to connect the site provisioning service to [Curo365](https://www.curo365.com). Configure the connection to the Azure queue and map the fields to a sharepoint column. The site provisiong service will be notified whenever a new item has arrived in the azure queue. When an error has occured during the handling of the message from the queue, the message is moved to the DeadLetterQueue.

When matters are successfully processed, the result json file will be uploaded to the SendQueue. Curo365 will parse the message and store the sharepoint url information in Curo365.

## Connection

Specify the Endpoint, SharedAccessKeyName and SharedAccessKey and the queue names. This information is delivered by Curo365.

*Debug*\
If enabled, the original message from the queue is added to the logfile.

## Mapping

Here's a sample json file that is created by Curo365. The fields can be mapped to the client or matter in DMSforLegal. Use the dot-syntax to specifiy a nested value, like Matter.Number

```json
{
    "Matter": {
        "Id": "e3d2499e-f204-eb11-a813-000d3a33f499",
        "Name": "Test Matter",
        "Number": "10000",
        "Type": "Administrative Law",
        "Description": null,
        "State": "Active",
        "Status": "Pending"
    },
    "Client": {
        "Id": "10f176f0-4270-ea11-a811-000d3a33febd",
        "Type": "account",
        "Number": null,
        "Email": "Clientservices@curo365.onmicrosoft.com",
        "Name": "Curo 365 Law"
    },
    "Responsible": {
        "Id": "4bd2b096-8ff7-ea11-a815-000d3a33f499",
        "Name": "Derek Mescheder",
        "Email": "dmescheder@curo365.net"
    }
}
```

*Client*\
Make sure the ClientCode is static and will not be changed in Curo365. Configure a default clientcode and clientname for matters that don't have a client (yet). Specify the mapping for ClientCode and ClientName and optional for other fields via the Client Mapping. For example: Client.Type=ClientType;Client.Email=Email (where ClientType and Email are fields available in the Clients List in Sharepoint.)

*Matter*\
Make sure the MatterCode is static and will not be changed in Curo365. Specify the mapping for MatterCode and MatterName and optional for other fields via the Matter Mapping. For example: Matter.State=MatterStage;Matter.Type=MatterType (where MatterStage and MatterType are fields available in the Matters List in Sharepoint.)

*TestMapping*\
If enabled, move the result client matter json to the Monitor\\Test directory and don't remove the message from the queue so it can be reprocessed.

## Dump Matters

In Curo365 (Dynamics365) the default functionality can be used to export the matter information to Excel. See [Dynamics365 documentation](https://learn.microsoft.com/en-us/dynamics365/customerengagement/on-premises/basics/export-excel-static-worksheet?view=op-9-1)
