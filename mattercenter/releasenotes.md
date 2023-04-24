# Release notes Epona MatterCenter SPFx

| **Date** | **Release** | **New changes** |
| --- | --- | --- |
| **21/10/2022** | 2.2.11.0 | White screen error after saving AI properties for some documents:fixed|
| **14/10/2022** | 2.2.10.0 | The search box: both clicking the clear button as removing a search text do not recover the filter.|
| **12/10/2022**|2.2.9.0|   The search for the common search box only starts after pressing enter|
|||Errors on some of the documents when trying to save the document type:fixed|
| **5/10/2022**|2.2.8.0| The preview remains visible as long as the mouse is over the preview |
| **4/10/2022**|2.2.7.0| The save button doesn’t always disappear after clicking  |
|||Tooltip save button correction|
|||Keep preview visible as long as the mouse isover the preview|
| **29/09/2022**|2.2.6.0| Automatic check-out/check-in when using AI save button |
|||Documents are loaded fist, then AI suggestions  |
| **29/09/2022**|2.2.5.0| Several AI suggestion improvements |
| **13/09/2022**|2.2.4.0| Files are downloaded when no peview available: fixed  |
| **13/09/2022**|2.2.3.0| Style changes for AI suggestions  |
| **7/09/2022**|2.2.2.0| SharePoint Tenant ID used for identification instead of setting in DMS Configuration |
|||Location of buttons colum can be configured|
|||Document preview on hover|
|||AI choices only visible when property exist on document|
| **26/08/2022**|2.2.1.0| Display AI assistance option on searching |
| **24/08/2022**|2.2.1.0| Configurable AI suggestions for metadata fields |
| **22/07/2022** | 2.1.48.0 | Open Matter Tab - Click on open matter tab and it will open external URL as well. I have added https and http keywords in the logic. If URL has https and http, then system will open the URL and if not then append tenant URL and open site URL. |
| **20/07/2022** | 2.1.47.0 | Display search suggestion based on filter configuration from the DMS configuration. |
| **01/07/2022** | 2.1.46.0 | Hide the parent term only display the child term. If no child term is there, then displaying the parent term. |
| **28/06/2022** | 2.1.45.0 | The deprecated nodes should not be listed in the dropdown, also the order should be by parent as it is more logical to see then grouped by parent.|
|||For tab filtration use can user query like this - PracticeArea eq General - Common. (example added in docscorpepona tenant.)|
| **28/06/2022** | 2.1.44.0 | The search query filter and display for common child name in metadata. Display logic is as follows: o If has parent then ParentTerm - ChildTerm o No parent then ChildTerm |
| **20/05/2022** | 2.1.42.0 | After search count issue in tabs |
| **16/05/2022** | 2.1.41.0 | Various small corrections |
| **15/04/2022** | 2.1.39.13 | Selection dropdown stays open to allow multiple selecteions.Will close on outside click |
|||Added the key (AdvancedSearch.QueryTextAddendum), to be able to configure where the document search should look|
| **14/04/2022** | 2.1.39.6 | Too many values in the Pie chart |
|||Combine two or more conditions for tab filter: && - for and query, \|\| - for or query|
|||Synchronize the search results and count with other tabs|
| **29/03/2022** | 2.1.39.5 | Clear the date-time field and allow a user to type the date |
|||Long text in the menu|
| **24/03/2022** | 2.1.39.4 | Display search suggestions in advance search based on and condition |
|||Add a new configuration for hiding the context menu items for the matters|
|||Search based on and condition|
| **01/03/2022** | 2.1.39.0 | Issue with custom date range in search panel resolved |
| **15/02/2022** | 2.1.37.0 | New configuration for hiding the tab: Navigation.Tab.[ActionName].IsHidden |
| **10/02/2022** | 2.1.36.0 | Edit functionality working on the matter archived tab |
| **08/02/2022** | 2.1.35.2 | Definition of list based tabs, like 'Archived Matters' |
| **28/01/2022** | 2.1.35.0 | Use of custom links in menu |
|||Date ranges in filters for custom dates|
|||(My)Matters counts ignore folders|
|||(My)Matters counts respect Chinese wall security settings|
| **06/01/2022** | 2.1.33.0 | Excel export now uses the xlsx format |
||| Search using multiple keywords possible |
||| LegalWord integration |
| **12/7/2021** | 2.1.32.0 | Reading custom columns from configuration issue resolved |
| **12/6/2021** | 2.1.31.0 | Possibility to use classic forms for adding and editing matters and clients |
| | | Sorting issue resolved (throttling error on some fields) |
| **11/5/2021** | 2.1.30.0 | History-back in browser on classic sites issue resolved: classic sites alwaysopen in new tab |
| | | Throttle issue resolved |
| **09/13/2021** | 2.1.26.0 | Folders where showing in Matters. Now fixed |
| **08/20/2021** | 2.1.25.0 | Main bar color stays white on classic page in full screen – resolved |
| **08/19/2021** | 2.1.24.0 | Request param functionality ?filter=... resolved |
| **07/30/2021** | 2.1.23.0 | Issue with custom fields in forms resolved |
| **07/29/2021** | 2.1.22.0 | Possibility to define tooltips for fields in forms |
| | |  Possibility to define default sortorder in lists
| **07/26/2021** | 2.1.21.0 | Reload button for when unrecoverable issue occurs |
| | | Hide and show field in form based on value in other field
| | Known issues | History-back in browser gives issue on classic sites. Set settings to open matters/mymatters/documents in new window to avoid the issue. |
| **07/09/2021** | 2.1.17.0 | Fatal error at startup resolved (related to not having an email address specified for the admin) |
| **07/07/2021** | 2.1.15.0 | Fatal error at startup resolved (related to choice or taxonomy fields not having values specified) |
| | | Resolved: When opening a Matter in same window, and then uses the history back button of browser, an error sometimes occurs |
| | | Resolved: No logging of errors yet to report server |
| | | Resolved: Error on Recent Documents when Hybrid or SharePoint is specified |
| **07/02/2021** | 2.1.14.0 | Fatal error at startup resolved (related to choice or taxonomy fields not having values specified) |
| | | No logging of errors yet to report server |
| | | Error on Recent Documents when Hybrid or SharePoint is specified |
| **06/22/2021** | 2.1.12.0 | When no user email is available, like for the EponaAdmin, the loginName is used instead |
| **06/18/2021** | 2.1.11.0 | Limited number of MyMatters resolved |
| | | Counting for MyMatters resolved |
| | Known issues: | When opening a Matter in same window, and then uses the history back button of browser, an error occurs |
| | | Errors occuring at start are not send to report server |
