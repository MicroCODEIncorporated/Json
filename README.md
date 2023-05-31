# Json.cs

The MicroCODE JSON Class. A public repository for development.

## Description

This is a simple, stand-alone C# .NET Class that can be added to any App to 
handle reading and writing JSON files. It is specifically intended to support
the persistent storage of App Settings in a JSON file (.json), but it can be used
for interfacing with any JSON data.

The current implementation supports 128 levels of nested Objects, including
nested Arrays. This can be changed with a single constant in the Class.

    /// <summary>
    /// The maximum number of nested objects and arrays allowed in a JSON file.
    /// Change this value to suit your needs.
    /// </summary>
    public const int NestedObjects = 128;

## Getting Started

Add the Json.cs file to your C# .NET App in Visual Studio or VS Code.
It has no depenciies beyond teh standard .NET libraries.

### Dependencies

    using System;           // for Event Handlers and Exception support
    using System.Drawing;   // for Color support
    using System.IO;        // for File IO
    using System.Text;      // for StringBuilder use in Exception logging
    using System.Threading; // for detecting ThreadAbortException

### Using the Class

This is a Static Class and does not require an object to be instantiated.

* Json.Write.*() -- methods making up the JSON GENERATOR.
* Json.Read.*() -- methods making up the JSON PARSER.


#### Wrting your App Settings to a .json

* Call the method to open a new .json with a complete path:

```
Json.Write.Open(App.SettingsFolder + App.Name + ".json");
```

* Call the method to open Root in the .json - this is optional but recommended:

```
Json.Write.Root();
```

* Set your JSON Object Name and call the method to open the Object in the .json:

```
objName = "App";  // use a varible for subsequent 'Member' calls
Json.Write.Object(objName);
```

* Write all the Member / Value Pairs to the  .json 
-- specifying the Object Name for integrity checks, where <_name> are your exisitng App variables:
NOTE: Our implementation stores ALL Member Values as STRINGS which are translated in the Json.cs code.
This allows us to store ANYTHING, dates, colors, Enums, etc.

```
Json.Write.Member(objName, "Version", _appVersion);
Json.Write.Member(objName, "Date", _saveDate);
Json.Write.Member(objName, "User", _userName);
Json.Write.Member(objName, "User Role", _userRole);
```

* Close your Object in the .json:

```
Json.Write.CloseObject();
```

* Close your JSON file:

```
Json.Write.Close();
```


#### Reading your App Settings from a .json

* Call the method to read the entire .json with a complete path:
-- this holds the .json file in memory, in the static class 'Json'.

```
Json.Read.Open(AppSpecific.JsonFileFolder + App.Name + ".json");
```

* Call the method to read past the Root in the .json - this is optional but recommended:

```
Json.Read.Root();
```

* Set your JSON Object Name and call the method to open the Object in the .json:

```
objName = "App";  // use a varible for subsequent 'Member' calls
Json.Read.Object(objName);
```

* Read all the Member / Value Pairs from the  .json 
-- specifying the Object Name for integrity checks, where <_name> are your exisitng App variables, 
"dafault value" is the string to return if teh Member is missing from the .json file.
NOTE: Our implementation stores ALL Member Values as STRINGS which are translated in the Json.cs code.
This allows us to store ANYTHING, dates, colors, Enums, etc.

```
Json.Read.Member(objName, "Version", "default value", out _appVersion);
Json.Read.Member(objName, "Date", "default value", out  _saveDate);
Json.Read.Member(objName, "User", "default value", out  _userName);
Json.Read.Member(objName, "User Role", "default value", out  _userRole);
```

* Close your JSON File:

```
Json.Read.Close();
```


## Help

Request help through our website: https://www.mcode.com 



## Terminology

| Word or Acronym	| Description/Definition                                |
|-------------------|-------------------------------------------------------|
|  JSON   	        | A text file holding JavaScript Object Notation.
|  Generator        | A code collection that creates a JSON file from App data.
|  Parser           |A code collection that creates App data from a JSON file.
|  CSharpSG         | MicroCODE's C# Style Guide. (Available on GitHub).



## Authors

Contributors names and contact info

* Timothy J McGuire [@tjmcode](https://github.com/tjmcode)


## Release History

* 0.0
    * 2023-05-30 - Initial Release within our Control.NET and Sequence.NET Apps
    * 2023-05-31 - Add support for up to 128 nested Objects and Arrays


## Future Development

* 0.n
    * New Feature: Handle Binary Data
    * Fix Defects: ...

## License

MIT License: MicroCODE.Json
Copyright © 2023
Timothy J McGuire, MicroCODE, Inc.
                       
