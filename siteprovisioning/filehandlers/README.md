# File handlers

When files are dropped inside the monitor directory the file is picked up by a specific handler based on the filename and extension. For excel both xls and xlsx are supported.

When the file is handled by the service, the file is renamed to: *active.*\<filename\>. When the handler is finished the file is moved to the completed or error directory.

