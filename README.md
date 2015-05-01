# FileMaker Guidelines

Our "style guide" for FileMaker Solutions

###IDs
use UUIDs. Either Get(UUID) or UUIDDecimal CF

###Plugins
BaseElements Plugin - too useful not to use on everything but FileMaker Go

###ExecuteSQL
You must use Custom Functions to save you from Field Name Changes

###Passing Multiple Parameters
Use JSON. There are now two JSON custom functions libraries, and a Script based modular FileMaker module to parse JSON. The one backed by BaseElements is the fastest and prefered, unless on FileMaker Go.

On Go use one of the other two JSON libraries. Unless you need serious speed to handle large JSON documents.  In that case you may need to use the pList set.

###Set Error Capture
Dont just turn it on.  Library and API scripts, ie scripts that are called by other scripts, should only use this if they have to surpress a specific error, and they should restore the error capture state after they are done.  They should always leave the error capture state the way they found it. They should show error dialogs ONLY if error capture is set to OFF

Buttons and other top level script turn on Error Capturing and handle errors appropriately.


###Modular Design
Use ModularFileMaker.orgs guidelines for exposing features as folders of scripts. Use a README script to describe module. Segregate scripts in to PUBLIC and PRIVATE FOLDERS

###Graph Organization
Use SELECTOR CONNECTOR for maximum graph flexibility and organization. 

If you are using a seperate data file or files, you don't have to use SELECTOR CONNECTOR in those data files