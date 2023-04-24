# Codex

This plugin is a post handler that will react on newly created json files from LegalSense plugin. It will generate xml files in the Codex API format for each LegalSense json created.

Copy the dll files from the Plugins\Codex directory to the site provisioning directory.  

Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Codex plugin.

Specify the following properties:

**Codex drop folder**
Folder where the plugin will store the generated xml files

**Codex to Legalsense matter mapping**
Specify the custom field mapping between Codex and LegalSense for the matter properties in the format `codexmatterfieldname=lsmatterfieldname`

If the *lsmatterfieldname* is not found, the value itself is used (see mapping sample 'Vestiging=MAIN_OFFICE').

To see all the possible legalsense matter fieldsname, set *Debug* to true and in the drop folder a json file will be created with all the possible fieldnames and values.

```json
{
  "access_kind": null,
  "aml_required": null,
  "archived_date": null,
  "archive_number": "",
  "real_archive_number": "",
  "billing_instructions": null,
  "billing_user": 4,
  "can_archive": false,
  "chinese_wall_kind": null,
  "client": 3,
  "client_reference": "",
  "custom_fields.Extranet": "",
  "custom_fields.dmsforlegal": "",
  "court_reference_number": null,
  "created_date": "2019-01-12T13:53:48",
  "date": "2019-01-12",
  "display": "XXXX / YYYY",
  "description": "",
  "docket_number": null,
  "engagement_letter_sent": null,
  "firm": 1,
  "invoice_language": "nl-nl",
  "is_billable": null,
  "is_recofa": false,
  "legal_aid_number": null,
  "matter_status": 1,
  "matter_type": 5,
  "modified_date": "2022-01-10T15:42:40",
  "magistrate": null,
  "name": "XXXX / YYYY",
  "number": "20190060",
  "office_expenses_rate": 0.0,
  "originating_user": null,
  "points": null,
  "practice_area": null,
  "practice_group": null,
  "reduction_rate": null,
  "referrer": null,
  "rvr_approval_date": null,
  "softkill_status": 1,
  "supervising_user": 4,
  "resource_uri": 1029
}
```

Een voorbeeld mapping:

```ini
DossierNummer=number
ExtraNummer=client_reference
Notaris=supervising_user
Behandelaar=billing_user
DossierCode=number
Opmerkingen=description
Betreft=name
Vestiging=MAIN_OFFICE
```

**Codex to Legalsense client mapping**
Specify the custom field mapping between Codex and LegalSense for the client properties in the format `codexclientfieldname=lsclientfieldname`;

If the *lsmatterfieldname* is not found, the value itself is used.

The xml client property "Achternaam", if mapped then the client will have attribute type "ClientNp" and a set of xml elements, else it will have type "ClientRp" with another set of xml elements. Please check the following example.

```json
{
  "alternative_names": "",
  "archived_date": null,
  "billing_instructions": null,
  "branches": [],
  "client_status": 1,
  "contact": 4,
  "create_date": null,
  "description": "",
  "is_billable": true,
  "is_identified": true,
  "modified_date": "2021-10-06T18:00:42",
  "name": "XXXXXXX",
  "number": "1003",
  "parent_client": 3,
  "originating_user": null,
  "reduction_rate": 0.0,
  "referrer": null,
  "sector": null,
  "softkill_status": 1,
  "resource_uri": 4,
  "account_manager_user": 4,
  "address_label_name": null,
  "addresses": [
    "/api/v1/address/3/"
  ],
  "attention": "",
  "bank_account_bic": "INGBNL2A",
  "bank_account_iban": "NL00INGB0123456789",
  "billing_cc_email": null,
  "billing_to_email": "invoice@xxxxx.com",
  "birthdate": null,
  "cellphone": "",
  "created_date": "2016-01-05T14:41:15",
  "coc_number": "12345678",
  "default_billing_address": 3,
  "default_contact_person": 5,
  "dunning_to_email": null,
  "has_dunning": null,
  "email": "",
  "email_2": "invoice@xxxx.com",
  "email_3": "",
  "email_4": "",
  "fax": "",
  "first_name": "",
  "gender": null,
  "initials": "",
  "invoice_language": "nl-nl",
  "invoice_send_method": 2,
  "is_debtor": true,
  "is_organization": true,
  "last_name": "",
  "name_prefix": "",
  "organization_name": "XXXXX",
  "payment_deadline": 14,
  "phone": "+31 00 123 45 67",
  "salutation": "",
  "tax_scheme": 1,
  "title": "",
  "vat_number": null,
  "website": "http://www.XXXXX.com",
  "address": "Postbus 123456",
  "address_kind": 1,
  "address_line_2": "",
  "address_template": 2,
  "city": "AMSTERDAM",
  "contact_person": null,
  "country": "Netherlands",
  "normalized_country": "NL",
  "department": "",
  "zipcode": "1000 XX"
}
```

Een voorbeeld mapping:

```ini
Email=email
Telefoon=phone
Adres.Straat=address
Adres.Postcode=zipcode
Adres.Plaats=city
Adres.Land=normalized_country
PostAdres.Straat=address
PostAdres.Postcode=zipcode
PostAdres.Plaats=city
PostAdres.Land=normalized_country
//ClientNp
Titel=title
Voornamen=first_name
Achternaam=last_name
Geslacht=gender
MobielNummer=mobile
//ClientRp
StatutaireNaam=organization_name
Handelsnaam=organization_name
```

**Matter filter**
Specify one or more filters in the format `lsfieldname=value`;
This filter makes the plugin only create xml files for data that is valid with the filter. Use the legalsense fieldnames and values. If the field name is not found, the client properties are also checked.
For example:
firm=1|2
This example filters for data that contains firm 1 or 2.

See [MatterList Filter](MatterList.md#filter) for more samples.

**Replace value**
use the site provisioning Replace value setting to replace values from LegalSense to valid codex values. Use the fieldname "Codex.{codexfieldname}" (see xml below). For example:
Codex.Behandelaar, replace value 4 with "LOGINNAME"
Codex.Notaris, replace value 4 with "LOGINNAME"

Example created XML file ClientNp

```xml
<?xml version="1.0" encoding="utf-8"?>
<Dossier xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <DossierNummer>20190060</DossierNummer>
  <ExtraNummer />
  <Notaris>4</Notaris>
  <Behandelaar>4</Behandelaar>
  <DossierCode>20190060</DossierCode>
  <Opmerkingen />
  <Betreft>XXX / YYYY</Betreft>
  <Vestiging>1</Vestiging>
  <OfferteTarief />
  <Clienten>
    <Client xsi:type="ClientRp">
      <ExtraNummer />
      <Hoedanigheid />
      <Email />
      <Telefoon>+31 20 123 45 67</Telefoon>
      <Adres>
        <Straat>Postbus 123456</Straat>
        <Huisnummer />
        <Postcode>1000 XX</Postcode>
        <Plaats>AMSTERDAM</Plaats>
        <Land>NL</Land>
        <Gemeente />
      </Adres>
      <PostAdres>
        <Straat>Postbus 123456</Straat>
        <Huisnummer />
        <Postcode>1000 XX</Postcode>
        <Plaats>AMSTERDAM</Plaats>
        <Land>NL</Land>
        <Gemeente />
      </PostAdres>
      <StatutaireNaam>XXXXX</StatutaireNaam>
      <Handelsnaam>XXXXX</Handelsnaam>
      <Zetel />
      <Rechtsvorm />
      <KvkNummer />
    </Client>
  </Clienten>
</Dossier>
```
