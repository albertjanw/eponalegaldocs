# View sets

Create one or more views that can be used inside the doclib. To specify an ordering, use the following syntax in the *OrderBy* property. Use the same fieldnames as in the *Fields* property. Specify multiply fields on multiple lines.

*FieldName\
FieldName ASC\
FieldName DESC*

To specify a query create a CAML query and copy the XML WHERE part.

*Tip:* to create the CAML query create the view inside sharepoint and use the SharePoint Online Client Browser to copy the CAML. See <https://spcb.codeplex.com/>
