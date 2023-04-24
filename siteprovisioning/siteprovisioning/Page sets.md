# Page sets

Create one or more pages in a 'template' modern site collection.

Inside the O365 Group set select the pageset. At runtime the template page will be copied to the O365 group (when created or updated). Each webpart can be configured with dynamic settings using the {} naming convention.

When the page contains two identical webparts, the ordering on the page should also be the ordering in the configuration.

## Text webpart

The HTML can contain dynamic text. For syntax reference see <https://sharpscript.net/>

- Delve

You can add a link to the personal Delve page for a specific user by using the variable {UserID:\<property\>}. The property should contain a value that can be resolved to a user (like full name or email address)\
For example:\

~~~html
<a href=\'https://delve.office.com/?u={UserID:RTK}&v=work\'\>Delve\</a\>
~~~

- User DisplayName

To convert an emailaddresses value into a displayname use {DisplayName:\<property\>}. This also works for when multiple emailaddress are stored in the property.

- Date

This sample shows N/A where there's no date and show a formatted date value if a date is available.

~~~text
{{#if isnull(OpenDate)}}N/A{{else}}{{OpenDate | toDateTime | dateFormat('yyyy-MM-dd') }}{{/if}}
~~~

- Conditional Link

~~~html
{{#if isNullOrWhiteSpace(ClientCode)}}
 N/A
{{else}}
 <a href='https://server/client?client_id={{ClientCode}}' target='_blank'>{{ClientName}}
 </a>
{{/if}}
~~~
