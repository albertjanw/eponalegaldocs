# Document sets

You can defined one or more documentset templates. To use documentsets:

- Enable the site feature DocumentSet, this will add a default DocumentSet contenttype.

- Define a new contenttype, using the DocumentSet as a parent contenttype (use the correct language for the parent contenttype name).

- Add the new contenttype to the document library

In the definition of the contenttype template, specify:

- The name of the DocumentSet

- The name of the contenttype

- One ore more allowed contenttypes (DMS Document / DMS E-mail)

- SharedFields, add all the fields that should be assigned to the documents that are stored in the documentset.

- Add one or more additional default values, for example DocumentType = Contract. The fields that already have a default value (via the doclib) should not be specified.

The last step is adding the documentset(s) with the documentlibrary set.
