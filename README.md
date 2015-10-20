# JSDependencies
This tool is a simple JS dependencies manager.
It simply allows you to load asynchronously multiple scripts and when dependecies are valid, execute it as soon as possible.

It only consists on 2 methods:

1. `Dependencies.add(<scriptName>, <scriptPath>, <scriptDependencies>)`

 *Add a script to load with specific infos*
 * scriptName: A simple string (unique) to describe the script. It'll be used in dependencies lists.
 * scriptPath: Full path to the script, URI or relative path, as a classic script.
 * scriptDependencies: Array of scriptName required before this one can be parsed.
2. `Dependencies.init()`

 *Fetch all the previous added script. It's the final method to call and it's required to work.*

Example:
```
Dependencies
	.add("MomentJS", "https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.10.6/moment.min.js")
	.add("jQuery", "https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js")
	.add("Bootstrap", "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js", ["jQuery"])
	.add("Angular", "https://ajax.googleapis.com/ajax/libs/angularjs/1.3.12/angular.min.js")
	.add("Angular-Bootstrap", "https://cdnjs.cloudflare.com/ajax/libs/angular-ui-bootstrap/0.14.2/ui-bootstrap.min.js", ["Angular", "Bootstrap"])
	.add("App", "script/app.js", ["Angular", "MomentJS"])
	.add("Script", "script/script.js", ["jQuery", "MomentJS"])
	.init();
```
