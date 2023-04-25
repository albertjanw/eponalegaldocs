# Create or update ClientMatter (json)

Use this format to create or update a clientmatter. The filename should contain *ClientMatter* and the format is json. See the sample directory for an example of the json file.

When a new clientmatter\*.json file is saved to the monitor directory from the various plugins, a check is done to make sure the client matter is new or changed. Before saving the new clientmatter file, the following check is done.

- Check if the same filename already exists in the Monitor directory.

- Check if the filename with the prefix *active.\<filename\>* already exists in the Monitor directory.

- Check if the same filename (removing the \_\<timestamp\> suffix) already exists in the Monitor\\Completed directory

- If an existing file is found, compare the content of the file with the new content from the new file. If the content is equal, don't create a new clientmatter.json file and skip the update.

See 3.20.1 ClientMatter Excel for more information

If the URL column in the matterlist for the matter is empty, the executed actions are handled the same as for new matters.
