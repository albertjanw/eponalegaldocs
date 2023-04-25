# ContactManager SOAP Api

The contactmanager api is available using the url ```http://<server>/api/contactmanager.asmx```

Existing actions are never changed. Newer methods are created using an
incrementing number.

The WSDL can be requested via: ```http://<server>/api/contactmanager.asmx?WSDL```

A request to the API will store two cookies in the response (CMAuth and
CMAuthentication). Resend this cookie with the next requests.

## Login

### Forms Authentication

Use the Login action:

```
<Login xmlns="http://epona.nl/ContactManager/">
      <userName>string</userName>
      <password>string</password>
</Login>

```

### Windows Authentication (NTLM)

Specify the windows credentials in the SOAP requests. It's still
necessary to use the login method, in this case only specify the
loginname (including the domain name). The password can be left empty.

## Fetch information

### SearchContacts

This request will return an array of *Item* objects, because the result
can contain multiple types of contacts.

```
<SearchContacts xmlns="http://epona.nl/ContactManager/">
      <searchType>string</searchType>
      <searchValue>string</searchValue>
      <numberOfRecords>int</numberOfRecords>
    </SearchContacts>
```

SearchType: Contact, Company, Employee, Person, CompanyDepartment

SearchValue: a search string like you enter in the left bottom search
panel inside the CM user interface

NumberOfRecods: the number of records that are returned.

Use the ItemType in the result *Item* object to identify the type of
record and use the specify
*Get*Company/GetEmployee/GetPerson/GetCompanyDepartment to fetch all the
details if necessary.

### Get\* actions

Use the different actions to fetch a single record from ContactManager.

### GetContactByExternalID

Fetch a single contact by using the unique external identifier.

Type: Company / Person / Employee / CompanyDepartment / Contact

Application: the name of the external application

ExternalID: the unique ID

```
<GetContactByExternalID xmlns="http://epona.nl/ContactManager/">
      <type>string</type>
      <application>string</application>
      <externalID>string</externalID>
    </GetContactByExternalID>
```

## Store information

### Get\* methods

The ID parameter should contain one of the following values:

- CM ID, the internal unique CM ID

- The external unique identifier in the format of APPLICATION\@ID (for
    example QUBIS\@1003)

- Leave the field ID empty.

CM will try to find the record using the supplied values. If not found
an empty record is returned with an empty ID property. If a record is
found the record is returned and the ID is filled with the CM ID.

### Save\* methods

To update a record **always** use this sequence:

- Fetch the record using the Get\* methods, an empty entity is
    returned when the record is not found.

- Save the record using the Save\* methods.

When creating a new record the Get\* method is not necessary. Fill the
*ID* field with the CM ID (returned from the Get method) or use the
external unique identifier in the format of APPLICATION\@ID.

Update the properties in the result object and send the object to CM
using the Save\* actions.

When the record is fetched the *VersionID* will contain the latest
version from the server. This value will be used to prevent concurrent
updates. To disable this behavior set *VersionID* to 0.

### Update Reference properties

Reference properties can be updated by supplying *one of these* values:

- CM ID, the internal unique CM ID

- A external link in the format of:\
    \<Application\>@\<ExternalID\>\[@\<ExternalCode\>\]\
    The externalcode is only used for a person or company to specify the
    clientcode.

- For LookupItems (like language, country, mattertype, etc) specify
    the *Code* as used in CM (see CRM Configuration, tab LookupItems)

- For internal employees the column *Extra* can be filled with the
    username, if the column extra is filled, leave the column ID empty.

### SavePerson2

If the person is not found an existing person is search based on a 100%
match on the properties (lastname, gender, lastnameprefix,
firstname/initials, emailaddress).

The *Owner* and *OwnerSub* properties can be updated by specify the
contact using the *ID* field or specify the windows username in the
*Extra* field (and make the ID field empty).

### SaveCompany2

If the company is not found an existing company is searched based on a
100% match on the properties (DUNS Number, Chamber of Commerce number,
website, RSIN number or Tax number).

The *Owner* and *OwnerSub* properties can be updated by specify the
contact using the *ID* field or specify the windows username in the
*Extra* field (and make the ID field empty)

### SaveAddress2

The external identifier should be unique over all addresses. For example
use a combination of the clientID + AddressType to generate a unique
identifier.

CM can automatically parse the streetline into street, number and
extension. Set the *StreetLine* property and leave the *Street* property
empty.

Specify the client (person or company) using the *ContactID*, for
example in the format of APPLICATION\@ID.

CM does NOT validate the address using the country requirements.

A new location is automatically created if an existing location is not
found using *LocationID* and a *LocationCode or LocationName* is
specified.

The fields *IsDefaultPostalAddress* and *IsDefaultVisitorAddress* are
only used when the value is set to *true*. When an address is no longer
default, make another Address the Default address. This will disable the
default setting for the previous default address.

### SaveEmployee2

The external identifier should be unique over all employees. For example
use a combination of the clientID + incrementing number to generate a
unique identifier.

A new department is automatically created if an existing department is
not found using *DepartmentID* and a *DepartmentCode or DepartmentName*
is specified.

The nested company and person properties are NOT saved to the company or
person in CM. Use a separate SaveCompany/SavePerson to modify the
person/company fields. Only the Person.ID and Company.ID fields are only
used when creating a new employee.

### SaveMatter3

Specify the correct *ActivityType* for a new matter (MATTER / MATTER_NOT
OR MATTER_ADV (can be changed in each implementation)). The permissions
on the matter are based on this property when creating a new matter (not
when updating).

*ClientContactID* can optionally contain a unique reference the client
contact (employee) for the matter. Specify the client (person or
company) using the *ClientID* (see Update reference properties)

## ContactManager REST Api

Some methods are also available as REST API that will return a json
object. To use the REST API make sure an authenticated session is active
by logging in.

The prefix for the url is ```https://\<url\> /api/contactmanager.svc/\*```.

For example: ```https://\<url\>/api/contactmanager.svc/SearchContactsByEmail?email=...```

## HTTP POST

### Login

/api/contactmanager.svc/Login?username=\<user\>&password=\<password\>

Will return true or false

## HTTP GET

### Search by Email

```\<url\>/SearchContactsByEmail?email=\<email\>```

Return one or more contacts with an exact match on the email address.
This will return an array of contact objects.

```
[{
 "AddressSummary": "",
 "AddressSummaryLong": "",
 "DisplayName": "",
 "EmailAddress": "",
 "Extra": null,
 "FaxNumber": null,
 "ID": "5043",
 "IsFolder": false,
 "LocationName": "",
 "MobileNumber": "",
 "ObjectType": "",
 "PhoneNumber": "",
 "Website": ""
},….]
```

## Search by Phone

```\<url\>/SearchContactsByPhone?phone=\<email\>```

Return one or more contacts with an exact match on the email address.
This will return an array of contact objects.

## Load single entity

```
<url>/GetItem/<ID>
<url>/GetContact2/<ID>
<url>/GetPerson2/<ID>
<url>/GetCompany2/<ID>
<url>/GetEmployee2/<ID>
<url>/GetMatter3/<ID>
<url>/GetAddress2/<ID>
```

Return an entity with the specific details.
