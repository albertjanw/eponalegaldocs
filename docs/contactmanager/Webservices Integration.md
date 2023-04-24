# Webservices Integration

For additional background information see
<https://ws1.webservices.nl/documentation>

**Configuration**

Config\\Webservices.config

**Timeout** (5)

number of seconds when the request is timed-out. The next request is
done to the backup url (url2). Second failure results in an exception in
the browser

**Username/Password** (empty)

Specify the username/password. Don't use the admin account.

*Important! When the updateservice is enabled, tracking is done per
username**.** Create a separate account for test environment and disable
the updateservice for that account (and disable the updateservice for
that account)*

**BusinessType (**ChamberOfCommerceV3)

The type of import that is currently active. Current options:

- ChamberOfCommerceV2 (BIK)

- ChamberOfCommerceV3 (default, SIC)

- Gradyon

**CreateLegalFormIfNotFound** (true)

If an entitytype (nv/bv/etc.) doesn't exists in ContactManager, it will
be created.

**CreateIndustryCodeIfNotFound** (true)

If an industrycode (bik/sic) doesn't exists in ContactManager, it will
be created.

**CreatePersonnelFullTimeNotFound** (true)

If an company employee size doesn't exists in ContactManager, it will be
created.

**DisableImportIndustryCode**(false)

If true don't import IndustryCode.

**SearchExteralInfoIndustryCode** (false)

Use the External Info (application = WEBSERVICES) to find the
IndustryCode (and fallback to Code)

**SearchExteralInfoEntityType** (false)

Use the External Info (application = WEBSERVICES) to find the EntityType
(and fallback to Code)

**SearchExteralInfoEmployeeSize** (false)

Use the External Info (application = WEBSERVICES) to find the
EmployeeSize (and fallback to Code)

**AddressNlEditable**(false)

If true, every user can manually edit an address with country NL
(administrators can always edit manually)

**AddressIntEditable**(true)

If true, every user can manually edit an address with country other than
NL (administrators can always edit manually)

**AddressNlManual**(false)

If true, every user can manually create a new address with country NL.
(administrators can always edit manually)

**AddressTypeCorrespondence**(empty)

The code for the address type for a postal address.

**AddressTypeEstablisement**(empty)

The code for the address type for a visitor address.

**ChamberOfCommerceSubDossierSplitCharacter** (.)

The character that's used between the *dossier / subdossier*

**IsCompanyEnabled** (true)

If false, search / importing new companies is disabled. Address lookup /
import is always active

**EnableUpdateService**

If true, every day a check is done to see if there are any updates to
registered chamber of commerce entities. Update are automatically
imported and are ready to be reviewed before applied to the company.

## Update Service

Updates are not tracked by webservices by default. It must be enabled
for the account that is specified in the config file. Use
<http://www.webservices.nl/nl/26/contact> to request activating this
service for a particular user.

Technical details can be found on
<https://ws1.webservices.nl/documentation/files/service_business-class-php.html#Business.Business_update_service_methods>

If the UpdateService is enabled in ContactManager every company that's
imported via the webservices is automatically registered for updates.

You can manually add / remove registered chamber of commerce numbers by
using the Import file ImportChamberOfCommerceUpdateService. The
**Action** column in the import file can contain. The default action is:
track the company for further updates (no credits charged)

- Remove / 1 remove chamber of commerce from tracked companies (no
    credits charged)

- Update / 2 import latest version from webservices, don't activate
    tracking (normal credits for "new company" are changed!)

- AddAndUpdate / 3 import latest version from webservices and track
    the company for further updates (normal credits for "new company"
    are changed!)

Every day a service will check if there are updates (if enabled in the
webservices.config) available for the tracked chamber of commerce
entities.

Updates are never applied directly to ContactManager. An email is sent
to the datamanager when updates are found. The updates are queued and
can be manually merged with the company using the CRM Configuration tab.

## Field Mapping

When a company is imported in ContactManager the following fields are
imported:

  |**CM** | **Webservices** |
  |---|---|
  |Name  |                                 trade_name_45 or legal_name|
  |OfficialName     |                      legal_name|
  |PreviousName       |                    trade_names|
  |PhoneNumber    |                        telephone_number|
  |MobileNumber  |                         mobile_number|
  |Website      |                          domain_name|
  |DateOfIncorporation |                   founding_date|
  |ChamberOfCommerce  |                    dossier_number|
  |ChamberOfCommerceEstablishmentNumber |  establishment_number|
  |ChamberOfCommerceOffice      |          chamber_number|
  |PostalAddress       |                   correspondence_*|
 | VisitorAddress    |                     establishment_*|
  |RSINNumber      |                       rsin_number|
  |TaxNumber       |                       rsin_number + B01|
  |CompanyEmployeeSize      |              ­class_personnel|
  |EmployeeCount      |                    Personnel|
  |ContactType BankRupt       |            indidication_bankruptcy|
  |ContactType In Possession    |          indicication_dip|
  |EntityType        |                     legal_form_code|
  |IndustryCodes    |                      Primary_sbi_code, secondary_sbi1 en 2|
|
  |MemberOf                  |             structure_ultimate_parent|
