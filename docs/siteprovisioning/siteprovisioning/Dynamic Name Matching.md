# Dynamic Name Matching

Each configuration object is configured with a name. The set name inside the json or excel file can contain variables. The variables can contain the title of the specific Sharepoint object (use {Title}) or one or more additional properties. Use the syntax {\<name of property\>} (case insensitive).

{yyyy} or {yy} is replaced with the current year.

{yyyy+1} or {yy+1} or {yy-3} is replaced with the current year +/- X (max value = 12)

{mmmm}, {mmm}, {mm} or {m} is replaced with the current month

{mmmm+1}, {mmm+1} or {mmm-3} is replaced with the current month +/- X (max value = 12)

{dddd}, {ddd}, {dd} or {d} is replaced with the current day

## Set Name Matching

Example:

Client{ClientCode}, ClientCode = 123

At runtime the {ClientCode} is replaced by the clientcode from the additional properties. The service will try to find a set with the name of *Client123* and if not found *Client*

Matter{MatterType}, MatterType = Tax

At runtime the {MatterType} is replaced by the MatterType from the additional properties. The service will try to find a set with the name of *MatterTax* and if not found *Matter*

Client{ClientCode}{MatterType}, ClientCode = 123, MatterType = Tax

The service will try to find a set with the name of Client123*Tax*, if not found *Client123*, if not found *Client*

*Doclib{MatterType},* Title = SecureDocs, MatterType = Tax

The service will try to find a set with the name of *DoclibTax\_*SecureDocs, if not found *DoclibTax*, if not found *Doclib*

*Doclib{Title}{MatterType},* Title = SecureDocs, MatterType = Tax

The service will try to find a set with the name of *Doclib*SecureDocs*Tax\_*SecureDocs, if not found *Doclib*SecureDocs*Tax*, if not found *Doclib*SecureDocs, if not found *Doclib*

## Replace value

Via the settings, Dynamic Names values, in the configuration custom values can be assigned for each field. This can be used to translate values from *'Gesloten'* to '*Closed'*. Specify the name of the field and for each field specify an old value and new value. The new value is used in the dynamic part of the property.

*UnknownValue*\
If a value (not empty!) is not found in the mapping, a default value can be returned by enabling *UseUnknownValueIfNotFound* and specifying a default value via *UnknownValue.*

*DefaultValueIfEmpty\
*If the value is empty, optionally specify a default value that should be used.

Use the prefix *Title* ("Title.\<fieldname\>") to only replace a value when the variable is used in a title field (matterlist/site(collection)).

It is also possible to configure a replacement of a character by specifying the name as ```:``` and a replacement value as: ```/```.

An example: a multilevel taxonomy field is used in the mattername, the : should be replaced with a ```/```.

FieldName: Title.MatterType\
Mapping:
name: ```:```
value: ```/```

The result is that a value of "NL:Tax" is converted to "NL/Tax" when the variable {MatterType} is used in the Title.

It's also possible to enable use the configured replace value when a client matter json file is parsed. Use the following prefixes:

ClientMatterDesign [Example](../sample%20configuration/Dynamic%20Client%20Matter%20Design.md)\
ClientMatterServerRelativeUrl\
PageTemplateUrl\
MatterListFolderName\
Office365GroupChannelName\
Office365GroupVisibility\
SiteCollectionTemplate\
DoclibCompliance\
ImportDocumentsFromTemplate\

Examples:

- [Dynamic replace value](../sample%20configuration/DynamicReplaceValue.md)

## Username/Group name

User and group names can contain variables that are replaced at runtime.

When Sharepoint online is used, the English names can be used for the built-in groups 'Everyone' and 'Everyone except external users'. At runtime these names are translated into the correct language of the current web.

Via Settings *Replace User/group names* you can specify an old and new name in the format:\
nl\\lang=marcel.lang\@epona.com

It's also possible to specify an external text filename, use the extension .txt. Copy the content to a text file and specify a the file path relative to the installation directory in the setting.
