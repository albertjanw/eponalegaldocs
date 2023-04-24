# Report an issue

When resolving issues/errors we need information from the browser developer tools. The browser developer tools can be opened by pressing F12 or CTRL-SHIFT-I (or via the menubar)

Errors are logged to the Console tab. Sharepoint and/or other extensions will also log items to the console. Only messages from epona are caused by Epona365. See example

![](./assets/ReportAnError_2022-11-25-10-36-26.png)

Errors (or wrong results) can also be caused by network errors. Each network request is logged to the network tab. To minimize the number of request activate the filter *Fetch/XHR*

![](./assets/ReportAnError_2022-11-25-10-39-58.png)

Here's an example:

![](./assets/ReportAnError_2022-11-25-10-41-22.png)

To view the details of the request click on the line. *Postquery* is a request to fetch results from the Sharepoint search engine.

![](./assets/ReportAnError_2022-11-25-10-42-55.png)

You can copy the *HiddenConstraints* and/or *QueryText* text and execute the search within Sharepoint using the normal Search user interface and validate the results (and/or tweak the query to get the correct results).

The request details can be copied via the tab *Payload*, right click, copy object

![](./assets/ReportAnError_2022-11-25-10-49-56.png)

When reporting an issue:

- describe the steps to reproduce (including screenshots/screencast (for example using [ShareX](https://getsharex.com/))
- check the console tab and copy Epona365 related messages
- check the network tab and copy the Payload
