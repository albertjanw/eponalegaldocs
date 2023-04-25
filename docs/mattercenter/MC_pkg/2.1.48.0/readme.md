# Latest Epona MatterCenter package (2.1.48.0)

![](../EponaMC_logo.png)

|New Changes (from earlier version 2.1.43.0)|
--- |
| Open Matter Tab - Click on open matter tab and it will open external URL as well. I have added https and http keywords in the logic. If URL has https and http, then system will open the URL and if not then append tenant URL and open site URL. |
| Display search suggestion based on filter configuration from the DMS configuration. |
| Hide the parent term only display the child term. If no child term is there, then displaying the parent term. |
| The deprecated nodes should not be listed in the dropdown, also the order should be by parent as it is more logical to see then grouped by parent.|
|||For tab filtration use can user query like this - PracticeArea eq General - Common. (example added in docscorpepona tenant.)|
| The search query filter and display for common child name in metadata. Display logic is as follows: o If has parent then ParentTerm - ChildTerm o No parent then ChildTerm |

[Download latest package](<https://download.eponalegal.com/s/5mdhN6WMEGIxYkdB/en_US?dir=%2FMC%2F2.1.48.0&node-id=44448>)
