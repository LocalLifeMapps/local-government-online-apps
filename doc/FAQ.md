[host an app on my server]: markdown/HowToHostAppOnYourServer.md
[host an app on online]: markdown/HowToHostAppOnOnline.md
[how the project is organized]: markdown/HowProjectIsOrganized.md
[app configuration file]: markdown/UnderstandingConfigurationFile.md
[JavaScript files organized]: markdown/HowJavaScriptFilesAreOrganized.md
[create a custom template]: markdown/HowToCreateCustomTemplate.md
[search for geocoded addresses]: markdown/HowToSearchForGeocodedAddresses.md
[search indexed feature layers]: markdown/HowToSearchIndexedFeatureLayers.md
[show a splash screen]: markdown/HowToShowSplashScreen.md
[sample of invalid JSON]: markdown/images/invalidJSON.png "sample of invalid JSON"
[sample of JSLint check of invalid JSON]: markdown/images/invalidJSONLinted.png "sample of JSLint check of invalid JSON"
[lint]: http://en.wikipedia.org/wiki/Lint_(software)
[JSLint]: http://www.jslint.com/
[js.LGTitleBar]: http://localgovtemplates2.esri.com/support/local-government-online-apps/doc/js2_doc/js.LGTitleBar.html

[nls/ folder]: ../nls/
[Resources]: markdown/Resources.md
[Esri Support]: http://support.esri.com/
[LICENSE.txt]: ../LICENSE.txt

![](markdown/images/gettingStarted.png)

## Frequently-Asked Questions (FAQ)

Additional information is available on the [Resources][] page.

### Getting Started
- [How do I host an app on my server?](#hostserver)
- [How do I host a configured app in ArcGIS Online?](#hostonline)
- [Can I host these apps in a secure environment?](#secure)

### Understanding the project
- [How is the project organized?](#projectorg)
- [What is inside an app configuration file?](#appconfig)
- [How are the JavaScript files organized?](#jsorg)
- [Why don't you put comments in the configuration file?](#comments)
- [Why don't you wrap the long "styles" lines in the configuration file?](#longstyles)
- [Why the emphasis on linting JavaScript and JSON?](#linting)

### Configuring
- [How do I create a custom template?](#createcustom)
- [How do I search for geocoded addresses?](#geocoded)
- [How do I search indexed feature layers?](#searchindexed)
- [How do I show a splash screen?](#splashscreen)

### Customizing
- [What is customization?](#custom)

----------
### Getting started

#### How do I host an app on my server?<a name="hostserver"></a>
Whether you are choosing to deploy these apps on your own server or are just using your server to develop and test app configuration changes before installing them in your ArcGIS Online organization, these instructions show you how to set up the project on your server. [More...][host an app on my server]

#### How do I host a configured app in ArcGIS Online?<a name="hostonline"></a>
Just because you've configured one of the Local Government Online apps using the configuration file doesn't mean that you have to host the app on your own web server. Learn how to host your configured app in your ArcGIS Online organization. [More...][host an app on online]

#### Can I host these apps in a secure environment?<a name="secure"></a>
Yes. Applications hosted and configured fully using ArcGIS Online take care of this for you automatically, but if you are hosting the app yourself in a secure environment, you'll need to update each reference to *http://* to the correct protocol, such as *https://*.


----------
### Understanding the project

#### How is the project organized?<a name="projectorg"></a>
The project consists of a small HTML file with general app JavaScript library that "plays" a JSON script to create the app's user interface. [More...][how the project is organized]

#### What is inside an app configuration file?<a name="appconfig"></a>
Each of the templates in the Solutions set of web apps is defined using the contents of an app configuration file. This file contains a pair of user interface configuration scripts that are "played" by a corresponding pair of JavaScript apps. One script is for the publication configuration app, which permits you to do fine-tuning configuration of the app as part of the publication process; the other script is for the web app itself. [More...][app configuration file]

#### How are the JavaScript files organized?<a name="jsorg"></a>
The JavaScript files are linted, documented, and compressed for syntax validation, ease of use, and speed of loading over the network, respectively. [More...][JavaScript files organized]

#### Why don't you put comments in the configuration file?<a name="comments"></a>

Inserting a comment into the the file would create invalid JSON, so we leave out comments to be able to use a validator. For more information, see [*Why the emphasis on linting JavaScript and JSON?*](#linting).

#### Why don't you wrap the long "styles" lines in the configuration file?<a name="longstyles"></a>

Inserting a line break into the styles string or concatenating strings would create invalid JSON, so we leave the string continuous to be able to use a validator. For more information, see [*Why the emphasis on linting JavaScript and JSON?*](#linting).

#### Why the emphasis on linting JavaScript and JSON?<a name="linting"></a>

In order to help catch typographic errors, all JavaScript and JSON in the repository is validated ("[lint][]ed") except for third-party libraries and the computer-generated language-specific phrase files in the [nls/ folder][]. That way, you have a known starting point for your modifications to files.

The value of linting can be illustrated by the following snippet of a configuration file. On a slow computer, you may not notice mistyping and it's very difficult for the web app to tell you the problem: the JSON parser that it uses just tells it that the JSON can't be interpreted -- the whole file is bad in some way.

![sample of invalid JSON][]

A linter will notice, however, and usually will be able to narrow the problem down to help you to fix it quickly. In this configuration file, I typed a period instead of a comma in the "config" structure of the [js.LGTitleBar][] component named "titleBar". This is an error that I made in the past, which, without a linter, would have taken a very long time to figure out. The error report below is from using [JSLint][] on this configuration file.

![sample of JSLint check of invalid JSON][]

See the [Resources][] page for information about validation.


----------
### Configuring

> Configuration hides/exposes/moves existing functionality only and these changes are supported by [Esri Support][].
> Apps with configuration changes may be hosted in ArcGIS Online or on your server.

#### How do I create a custom template?<a name="createcustom"></a>
If you're configuring an app beyond the optins available in the app's configuration panel and using ArcGIS Online to host the app, you'll need to store the configuration in a new web app template. Using this template, your users can publish web  maps to create web apps. [More...][create a custom template]

#### How do I search for geocoded addresses?<a name="geocoded"></a>
The standard app configurations search for text in feature layers, but are capable of using Esri's World Geocode Service or another geocoder to search for an address instead of, or in addition to, searching one or more feature layers. [More...][search for geocoded addresses]

#### How do I search indexed feature layers?<a name="searchindexed"></a>
The standard app configurations search for text in feature layers using a wildcard search with leading and trailing wildcard characters. This search matches any feature that has the search term in at least one of the search fields, which is very flexible, but also means that an index can't be used on the feature layer. By configuring the search to not use an initial wildcard, very large feature layers can be searched more efficiently. [More...][search indexed feature layers]

#### How do I show a splash screen?<a name="splashscreen"></a>
The apps have a help display that can be shown by clicking the help icon in the app's menu bar. The app can be configured to show this display by default when the app initially loads. [More...][show a splash screen]


----------
### Customizing

####What is customization?<a name="custom"></a>
> Customization modifies the core structure/functionality of the application and these changes are not supported by Esri Support.
> Apps with customization changes must be hosted on your server.


----------
Copyright 2013 Esri. Licensed under the Apache License, Version 2.0; a copy of the license is available in the repository's [LICENSE.txt][] file.
