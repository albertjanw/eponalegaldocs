# Jvris

This plugin is a file handler that will react on json files that contain the name jvrismatter and will parse the json into multiple json files with mapping on properties.
File name example: jvrismatter_20220722T142246.json.

Copy the dll files from the Plugins\Jvris directory to the site provisioning directory.  

Restart the service to activate the plugin.

Start the configurator and browse to CustomSettings to configure the Jvris plugin.

Specify the following properties:

**Client Code**
Json file property to match the sharepoint client code field, for example: CodEnt.

**Client Name**
Json file property to match the sharepoint client name field, for example: NomEnt.

**Client Field Mapping**
Optional field that maps json file client properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
For example: Group=GrcEntDes|NomEnt

**Matter Code**
Json file property to match the sharepoint matter code field, for example: CodDos.

**Matter Name**
Json file property to match the sharepoint matter name field, for example: NomDos.

**Matter Field Mapping**
Optional field that maps json file matter properties to sharepoint fields with syntax: sharepointname1=name1;sharepointname2=name2.
Use the character "|" for "or" conditions if null
For example: ClientGroup=GrcEntDes|NomEnt;Responsible=ResDos;MatterType=NomDepDos;MatterStage=DtaFechoDos;MatterClosedDate=DtaFechoDos
