# FileMaker Guidelines

Our "style guide" for FileMaker Solutions

Work in Progress. Links and example files to be added

### Nameing Conventions
Don't use tons of goofy characters, and no spaces in field names. Keep it simple. use a "z_" prefix to push non data fields to the bottom of the list.

### IDs
use UUIDs. Either Get(UUID) or UUIDDecimal Custom Function. See example file. https://github.com/geistinteractive/fmguidelines/blob/master/examples/UUIDs.fmp12

### Plugins
[BaseElements Plugin](http://www.goya.com.au/baseelements/plugin) - too useful not to use on everything but FileMaker Go

### ExecuteSQL
You must use Custom Functions to save you from field name changes

### Passing Multiple Parameters
Use JSON. There are now two JSON custom functions libraries, and a Script based modular FileMaker module to parse JSON. The one backed by BaseElements is the fastest and prefered, unless on FileMaker Go.

On Go use one of the other two JSON libraries. Unless you need serious speed to handle large JSON documents.  In that case you may need to use the pList set.

### Set Error Capture
Dont just turn it on.  Library and API scripts, ie scripts that are called by other scripts, should only use this if they have to surpress a specific error, and they should restore the error capture state after they are done.  They should always leave the error capture state the way they found it. They should show error dialogs ONLY if error capture is set to OFF

Buttons and other top level script turn on Error Capturing and handle errors appropriately.

### Logging Errors
Do it :-)

### Transctional Scripting
Use database transactions to ensure ensure that your scripts are handling your data safely. Use Commit and Revert to ensure that all edits are made or none of them are.

### Modular Design
Use ModularFileMaker.orgs guidelines for exposing features as folders of scripts. Use a README script to describe module. Segregate scripts in to PUBLIC and PRIVATE FOLDERS

### Graph Organization
Use SELECTOR CONNECTOR for maximum graph flexibility and organization. 

If you are using a seperate data file or files, you don't have to use SELECTOR CONNECTOR in those data files

### File Seperation
It can be useful, but it isn't necessary. Most people do it to avoid imports. So they seperate data from UI. But you can't completely avoid imports. And doing so complicates things like security. So data seperation to avoid imports is a dubious reason to seperate files.

The biggest benefit to seperation is to make things more modular. If you have a very complex solution, breaking things up into a set of smaller files can make a lot of sense. A lot of smaller things are alway easier to maintain then a larger thing.