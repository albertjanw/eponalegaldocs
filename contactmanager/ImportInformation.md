# Import Information

ContactManager can import information using standard excel files. There are several different imports each to import specific information. Each import has its own specification, but there are some general rules and features.

1. The first row of the excel files contains the fieldnames. The order of fieldnames is not important.
1. During the import records can be created or updated. The import always tries to find an existing record based on 3 or 4 columns. When a record already exists it will update that record, else it will create a new record:

- CM\_ID
  The internal unique (database-wide) ID number in ContactManager
- ExternalType\
  A fix value of:
  - P = Person
  - C = Company
  - E = Employee
  - CD = CompanyDepartment
  - A = Address
  - L = Location
  - D = Department
  - Client / CompanyPerson / PersonCompany = find contact of type person or Company
  - Full Name (like Person / IndustryCode / Industry), equal to TableName without prefix *do*.

Not used in every import, only if it’s unclear what the type of contact will be.

- ExternalApplication\
  The name of the external application that is used in a previous import to add records to ContactManager
- ExternalApplicationID\
  The ID in the external application that is used in a previous import to add records to ContactManager.
  If type is Employee, it’s possible to specify the company externalid and person externalid like this: 1234@@789 (1234 = company externalid, 789 = person externalid)

First of all the import always tries to find a record based on the CM\_ID. If the CM\_ID cannot be found, the import will try to find a record using the ExternalType, ExternalApplication and ExternalApplicationID information.

1. If the import contains lookup lists (like Country, Industry, etc.) the excel file should contain the **Code** of the lookup item (not the ID value).

There are global options when starting an import:

- mark record as changed
  If true the changed record is also marked as changed and (if available) changes will be synchronized to external systems if applicable.
- clear
  if true collections will be cleared before adding new items, resulting in replacing the information in Contact Manager with the information from the import file
- always update
  if true, all the property values of the record are always updated.
  if false, only the property values of the record that are empty are updated with values from the import file (if not empty).

When creating new records Contact Manager will automatically assign default permissions as specified in the web.config. If the current user is the *Administrator*, the default permissions will NOT be assigned.

## Import Contacts

This sheet can be used to import persons, companies and employees with address information.

*Person*\
If one of the following fields contains information the import assumes you want to update an existing or create a new person:

- PersonLastName
- PersonCM\_ID
- PersonExternalApplication AND PersonExternalID

If the import finds an existing person it will update the information ONLY if the *PersonLastName* is filled in, else the import will only use the existing person (and for example use it to create an employee).

If a single match is found on these criteria and the external information is empty, no new person is created:

- *LastName and (FirstName or Initials) and (BirthDate or Email)*
- *LastName and (FirstName or Initials) and (Street and City) or (Street2 and City2)*

*Company*\
When one of the following fields contains information the import assumes you want to update an existing company or create a new company:

- CompanyName
- CompanyCM\_ID
- CompanyExternalApplication AND CompanyExternalID

If the import has found an existing company it will update the information ONLY if the *CompanyName* is filled in, else it only will use the existing company (and for example use it to create an employee).

If a single match is found on these criteria and the external information is empty, no new company is created:

- DUNSNumber
- ChamberOfCommerce
- TaxNumber
- Website
- Name and (Street and City) or (Street2 and City2)

*Employee*\
If the import has create a new person (or found an existing person) AND it has created a new company (or found an existing company) it will automatically create an Employee (if an existing employee is not found).

The import process will try to detect if the employee is already exists by searching in the list of employees that are attached to the company.

If a single match is found on these criteria and the external information is empty, no new employee is created:

- EmailAddress  and LastName
- LastName and (FirstName or Initials)

*Department*\
If the import finds no existing department using the ID information (and/or *DepartmentCode* and/or *DepartmentName*) it will create a new department.

*Address*\
In this import you can import 2 addresses. The first address always becomes the default postal address. If a second address is imported it automatically becomes a visitor address.

If you want to import more address for the same contact, use the other *ImportAddresses* specification.

If you specify a LocationCode the addresses will be created inside the specified location, else the default location will be used.

The import process will check for an existing address (if the external information is empty) by comparing the *AddressLine, Street* and *City* fields. If an existing address is found, it will use the existing address.

*UserName*\
You can automatically create a new user when this column contains a value. For example to import the internal employees and automatically create users and setup a relation between the user and employee record.

If the password is not filled in, Windows Authentication will be used.

*FolderPath*\
Specify a folder path (with one or more levels) using a backslash or forward slash as separator. The import will try to find the folder from the Workspace. If the folder cannot be found a new folder will be (recursively) created. A shortcut will be placed inside this folder to the imported contact.

*FolderType*\
When this field is empty or contains the number 0 the import will create a normal *Contact Folder* with *contact shortcuts*, else it will create a *subscription folder* with *subscription items*.

*FolderPath* and *FolderType* can be added multiple times. Add a number (FolderPath1, FolderType1, FolderPath2, FolderType2, etc.) to specify multiple folders.

## Import Shortcuts

This format can be used to create a folder structure containing one ore more shortcuts (or subscription items) to contacts.

*Contact*\
Specify the ID information for the contact

*FolderPath*\
Specify a folder path (with one or more levels) using a backslash or forward slash as separator. The import will try to find the folder from the Workspace. If the folder cannot be found a new folder will be (recursively) created.

*FolderType*\
When this field is empty or contains the number 0 the import will create a normal *Contact Folder* with *contact shortcuts*, else it will create a *subscription folder* with *subscription items*. If the **FolderType** is a valid code for a *SubscriptionFolderType*, it will be assigned to the new folder.

*SubscriptionItemStatus*\
Optionally assign a new status (subscriptionfolder only)

*SubscriptionStatus*\
Optionally assign a subscriptionstatus (subscriptionfolder only) (Subscribed/Unsubscribed/Inherited/None)

*SubscriptionItemOwner*\
Optionally add an owner to the subscriptionitem (subscriptionfolder only)

## Import Addresses

This format can be used to import one or more addresses for a specific contact. The import process will check for an existing address by comparing the *AddressLine, Street* and *City* fields. If an existing address is found, it will use the existing address.

*Contact*\
Specify the ID information for the contact

*Employee*\
If the contact is an employee optionally import an addressline at employee level.

*Company*\
Add or use an existing location and update information

*Address*\
Import the address information, added to the location specified within the company. If location is not filled in the default location will be used.

## Import Photos

Use this format to add photo information to a person.

*Contact*\
Specify the ID information for the person

*Photo*\
Specify a full path and filename to the image that contains the photo. This should be a (local) path available on the server. Copy the photo’s to a specific directory on the server and specify the local path in the excel file.

## Import Contact Relations

Use this format to import relations between two contacts.

*From Contact*\
Specify the ID information for the contact

*ContactRelationType*\
The type of relation between the two contacts.

*To Contact*\
Specify the ID information for the contact

## Import DUNS-number / Chamber of Commerce number

Use this format to import the DUNS-number or Chamber of Commerce number for companies.

*Contact*\
Specify the ID information for the company

*Duns or Chamber of Commerce*\
The DUNS-number or Chamber of Commerce for the specified company

## Import Categories / Interests / Industries / IndustryCodes / Responsibilities

Use this format to import one or more lookup items that will be assigned to a specific contact. Before starting the import specify if the existing lookup items should be removed before adding the items from the excel file of that new lookup items should be added to the existing lookup items.

*Contact*\

Specify the ID information for the company

*Lookup Item*\
The code for the specific lookup item.

## Import Member Of

Use this format to import company structures (affiliates).

*Contact*\
Specify the ID information for the company

*Member of*\
Specify the ID information for the *member of the company*

## Import Owner

Use this format import the owner/account manager information for contacts

*Contact*\
Specify the ID information for the contact

*Owner UserName*\
Specify the user name (including domain name) that will be assigned as owner for a specific contact

## Import Employee Job information

Use this format import the employee job information for employees.

*Contact*\
Specify the ID information for the contact

*Job*\
Specify the job title and/or job function

## Import Outlook Folder Sync

Use this format to add or remove folders for one or more users that will sync to Outlook.

*Username*\
Specify the username

*FolderPath*\
Specify the folder path like ‘Afdeling/Sub Folder/Sub Sub Folder’

*Remove*\
Leave empty to add a folder, specify true to remove the folder for the specified user.

## Import Update

Use this format to update one or more fields. The following fields are used to identify a record in CM. The other columns that are added are assumed to be a valid field for that record. The value is only updated when the current value is empty or the option “Always overwrite” is enabled when importing:

|CM\_ID|Unique identifier in CM|
| :- | :- |
|CM\_Code|Used for Contact.ClientCode/Matter.MatterCode/LookupItem.Code, ExternalType is required!|
|ExternalType|Specify the type name (not necessary when CM\_ID is specified|
|ExternalApplication|Specify the name of the external application, only used in combination with ExternalType and ExternalApplicationID|
|ExternalApplicationID|Specify the externalid of the external application, , only used in combination with ExternalType and ExternalApplication|

## Import D&B information

Use this format import specific D&B information for companies.

*Important!!*

Put the (ultimate) parent company at the top of the excel file, so they are imported first.

*Contact*\
Specify the ID information for the company (child company). If no company is found, the DUNS, TaxNumber and Name/Street/City are used to find an existing company in ContactManager

*Name, OfficialName*\
These fields are only imported when an existing company is not found.

*Address*\
Import the address information (optionally including external information), added to the default location of the company. These fields are only imported when an existing company is not found. New address is only created if the combination of street and city does not already exist.

*Owner*\
Specify the user name (with/without domain name) that will be assigned as owner for a specific contact

*MemberOf*\
Specify the ID information for the parent company. If no company is found, the DUNS is used to find an existing company in ContactManager

If left blank the MemberOf / (Ultimate) Parent company is cleared (in combination with *Always Update*).

*MemberOfLocked*\
Enter a date or a boolean true value to indicate that the Member Of field is locked.

*MemberOfLockedUser*\
Specify the ID information for the User that is responsible for locking the Member Of Field.

*MemberOfComments*\
Specify the reason why the Member Of information is locked.

*SIC1-10*\
Specify one ore more SIC code. The SIC code will be added to the list. If the option *Clear* is selected, the current list of SIC codes are removed in ContactManager.

## Import Synchronisation Information

Use this format to import external ID information into Contact Manager.

*Entity*\
Specify the ID information for the *Entity*. In case of a lookup item you can also specify the (unique) *Code* of the lookup item in CM. *External Type* is required in case of specifying the record by *Code* or *Application/ExternalID*.

*External Information*\
The specified *Application, ExternalID* and *ExternalCode* will be added to the Entity in CM. If the *ExternalID* is left blank, the external information will be removed from the Entity

## Import DeDuplication actions

Use this format to import deduplication actions into Contact Manager.

*Master Entity*\
Specify the ID information for the *Master Entity*. *External Type* is required in case of specifying the record by *Code* or *Application/ExternalID*.

*Duplicate Entity*\
Specify the ID information for the *Duplicate Entity*. *External Type* is required in case of specifying the record by *Code* or *Application/ExternalID*.

*Action*\
Specify the type of action that should be executed to the Duplicate Entitity, None / InActive or Remove.

## Import Permissions

Use this format to import permissions and/or to create a folder structure with correct permissions into Contact Manager. When ‘clear collections’ is checked, each entity is resetted automatically to the default permissions (equal to PermissionType is ‘reset’).

*Entity*\
Specify the ID information for the *Master Entity*. *External Type* is required in case of specifying the record by *Code* or *Application/ExternalID*.

*FolderPath*\
Specify a folder path (with one or more levels) using a backslash or forward slash as separator. The import will try to find the folder from the Workspace. If the folder cannot be found a new folder will be (recursively) created.

*FolderType*\
When this field is empty or contains the number 0 the import will create a normal *Contact Folder* with *contact shortcuts*, else it will create a *subscription folder* with *subscription items*.

*PermissionType*\
*Reset*, reset the permissions on the entity (remove all permissions and enable inherited)

*ResetChilds*, reset the permissions on the entity and on all childs (for example folder and its childnodes) (remove all permissions and enable inherited)

*Allow*, the specified *user/role* name will get **Allow** *Permission* on the Entity

*Deny*, the specified *user/role* name will get **Deny** *Permission* on the Entity

*Remove*, the permissions specified with the *user/role* and *Permission* will be removed from the Entity.

This is the script to determine the permissions types

action = (GetFieldValue("PermissionType") as string ?? String.Empty).ToLower();

int allowed = -1;

cms.PermissionService ps = Session.GetService<cms.PermissionService>();

switch (action) {

``case "reset":

``node.Permissions.Inherit = true;

``node.Permissions.ResetPermissions();

``break;

``case "resetchilds":

``ps.RemoveChildPermissionsAndSetInheritFlag(node as cms.INode);

``break;

``case "deny":

``case "denied":

``allowed = 1;

``break;

``case "remove":

``case "removed":

``allowed = 2;

``break;

``case "allow":

``case "allowed":

``default:

``allowed = 0;

``break;

``}

*Inherited*\
*True/False*, enable / disable inherited permission on the entity. If empty, lease as is.

## Permissions

There is a set of pre-defined permissions supported internally by DataObjects.NET. Permissions are sometimes automatically assigned (for example if you have ownerpermissions, you have also readpermissions (see permissions between hives).

*DataObjects.NET.Security.Permissions*\
*AdministrationPermission** - this permission is supported internally by DataObjects.NET. It allows to perform anything - any permission Demand will be successful if this permission is allowed.

*ChangeFullTextDataPermission** is required to change any full-text indexing data (see IFtObject, FtRecord). It’s not necessary to assign this right to an user or role. It’s used by the system.

*ChangePasswordPermission** is required to use SetPassword method for the particular User;

*ChangePermission** is required to change any property of the DataObject instance;

(automatically assigned when OwnerPermission)

*ChangePermissionsPermission** is required to change the Permissions property of the DataObject instance;

(automatically assigned when OwnerPermission)

*ChildrenDeserializationPermission** is required to deserialize child objects of the DataObject instance. Not required.

(automatically assigned when OwnerPermission)

*ChildrenPermissionsDeserializationPermission** is required to deserialize child objects' permissions. Not required.

(automatically assigned when OwnerPermission)

*OwnerPermission** - the presence of this permission for a specific user (or group) tells that he is an owner of the DataObject instance (actually it implicitly grants ChangePermission, ChangePermissionsPermission, ReadPermission, ReadPermissionsPermission, RemovePermission, ChildrenDeserializationPermission, ChildrenPermissionsDeserializationPermission, SerializationPermission).

*SerializationPermission** is required to serialize the DataObject instance;

(automatically assigned when OwnerPermission). Not required.

*ReadPermission** is required to read any property of the DataObject instance;

(automatically assigned when OwnerPermission)

*ReadPermissionsPermission** is required to read the Permissions property of the DataObject instance;

(automatically assigned when OwnerPermission)

*RemovePermission** is required to remove the DataObject instance.

(automatically assigned when OwnerPermission)

Next to the pre-defined permissions there are a set of additional permissions:

*Xtensive.Cms.Permissions*\
*CreateChildNodesPermission** is required to create a new child within a node.

(automatically assigned when OwnerPermission)

*EnumerateChildNodesPermission** is required to read the child nodes of node

(automatically assigned when OwnerPermission, ChangePermission, ReadPermission)

*ReadSummaryInfoPermission** is required to read the main properties of a node

(automatically assigned when OwnerPermission, ChangePermission, ReadPermission)

*Guide.Crm.Permissions*\
*RemoveFolderPermission** is required to remove a contactfolder, subscriptionfolder and a contactsearchfolder.

*ChangeCompanyNamePermission** is required to change some specific properties of a company (Name, OfficialName, MemberOf, DUNSNumber, ChamberOfCommerce, Owner).

(automatically assigned when OwnerPermission)

*ChangeMarketingInformationPermission** is required to change some specific properties of a contact (Jobfunction, Categories, Interests, Industries, Responsibilities, StockExchanges, Segments, ContactType).

(automatically assigned when OwnerPermission)

*Summarize*\
create new items: **CreateChildNodesPermission;*\
create new folder: **CreateFolderPermission;*\
change important information: **ChangeCompanyNamePermission;*\
list items: **EnumerateChildNodesPermission;*\
remove items from folder: **RemoveChildNodesPermission;*\
verify: **VerifyPermission;*\
remove folder: **RemoveFolderPermission.*

## Import ChamberOfCommerce Update

Use this format to import chamberofcommerce information for the Update Service from webservices.nl.

More details can be found on [](https://ws1.webservices.nl/documentation/files/service_business-class-php.html#Business.Business_update_service_methods)

*Contact*\
Specify the ID information for the company

*ChamberOfCommerce*\
Specify the chamber of commerce number. Contact information is not needed in this case. The import will search for an existing company via the chamber of commerce number.

*Action*\
The following values can be used. The default action is: track the company for further updates (no credits charged)

- Track / 0 à Track the company for updates (no credits charged) (default action)
- Remove / 1 à remove chamber of commerce from tracked companies (no credits charged)
- Update / 2à import latest version from webservices, don’t activate tracking (normal credits for “new company” are changed!)
- AddAndUpdate / 3 à import latest version from webservices and track the company for further updates (normal credits for “new company” are changed!)

## Import Lookupitems

**(Academic) titles**\
When in the contact.config the following key are set:

```<add key="ViewPersonTitleList" value="Visible" />```

```<add key="ViewPersonPostTitleList" value="Visible" />```

It is possible to import (academic) titles and post titles:

|Type|Code|Name|ExternalApplication|ExternalApplicationID|ExternalApplicationCode|PersonPostTitle|
| :- | :- | :- | :- | :- | :- | :- |
|PersonTitle|DR|dr.|||||
|PersonTitle|RA|rA||||1|

**LookupFieldValue**\
To import LookupFieldValue linked to a parent lookupfield. Use the following columns

*Field*\
The code for the LookupField that the LookupFieldValue should be linked to

|Type|Field|Code|Name|ExternalApplication|ExternalApplicationID|ExternalApplicationCode|PersonPostTitle|
| :- | :- | :- | :- | :- | :- | :- | :- |
|LookupFieldValue|WWFT|WWFT_YES|WWFT Plichtig|||||

## Import SubscriptionStatusPermission

Optionally use the column *Subscribe* with a true value to update the contact to Subscribed.

## Add LookupFieldValue to an existing contact or matter

Use this import to link a lookupfieldvalue to an existing contact or matter.

*Contact* or *Matter*\
Specify the ID information for the Contact or Matter (using CM_ID or ExternalApplication columns)

*MatterCode*\
Optionally use the mattercode to link a lookupfieldvalue to a matter

*Code*\
Specify one or more Lookup Field Value codes (seperated by a ; or ,)
