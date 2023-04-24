# LeanLaw (Quickbooks)

This plugin will periodically query the LeanLaw API for new and updated information. It will start a query with a filter based on the "modified on" date.

To connect the following information is necessary:

- ApiKey

For more information about the API and web userinterface to test the GraphQL API, see the [LeanLaw API documentation](http://support.leanlaw.co/en/articles/5307735-how-to-use-leanlaw-s-public-api)

## LeanLaw Test

If the setting Test is enabled, the result client matter json is stored in the ./Monitor/Test directory. The LastRunDateTime is not updated!\
Use this mode to check the information returned from LeanLaw and the result mapping. All properties returned from LeanLaw are added ot the result clientmatter.json

## LeanLaw Mapping

Specify the fieldname from LeanLaw and the target (internal) SharepointName. The matching is case-insensitive.
Use the dot syntax to specify a nested value, for example

~~~text
status=MatterStage;primary.email=PrimaryEmail;primary.name=PrimaryName;fields.referralSource=Referral;
~~~

*LoadMatterUsers*\
If enabled, the matterUsers are fetched from the matter and dynamically converted into properties grouped by *Type*:

- IsPrimary  = Primary
- IsOriginating = Originating
- IsReviewer = Reviewer
  
The name convention is:

- MatterUsers{Type}Name\
the names of all the users where type is true
- MatterUsersNo{Type}Name\
the names of all the users where type is not true
- MatterUsers{Type}Email\
the emailaddresses of all the users where type is true
- MatterUsersNo{Type}Email\
the emailaddresses of all the users where type is not true

combined with the *Role* value.

- MatterUsers{Type}{Role}Name
- MatterUsersNo{Type}{Role}Name
- MatterUsers{Type}{Role}Email
- MatterUsersNo{Type}{Role}Email

Where {Role} is equal to:

- NONE
- PRINCIPAL
- LEAD
- PARALEGAL
- TIMEKEEPER
- OPERATOR
- ACCOUNTANT
