# dotnetconf 2017
my notes on www.dotnetconf.com

## 1. Keynote 

Starting with `dotnet cli`

1. How to check and change the version of dotnet core for a specific project. It can be done by changing the SDK version in the `global.json`.

![change SDL version](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/change_dotnet_skd_for_a_project.png)

2. Add existing projects as a reference by using ```dotnet add reference...```

![add project as a reference](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/dotnet_core_cli_add_existing_project.png)

3. When a project is created in the command line it doesn't have the sln file. If we want to work with VS we can create sln file and add the project to it

use `dotnet new sln` to create `sln` file inside the project folder

![create sln](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/dotnet_core_cli_to_open_proj_in_vs__create_sln-_ile.png)

use `dotnet sln add <your project>.csproj` to add the project to the solution

![add project to the solution](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/dotnet_core_cli_add_things_to_sln.png)

5. In C# 7.1 Main method can be made async 

![async main method](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/main_methods_now_can_return_tasks_to_be_async.png)

6. Mono and WebAssembly - to research here https://github.com/lrz/mono-wasm

![mono and webassembly](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/expose_csharp_to_the_browser.png)


## 2. What's new in APS.NET Core 2.0
    + Install .NET Core 2.0. from https://dot.net/core
    + Install VS from https://visualstudio.com

+ Get started faster

Create nwe project with `dotnet new web -o myapp` where `-o` is for output directory. the restore is already run for us so we don't have to run it manually. Most of the packages have been consolidated in `Microsoft.AspNetCore.All` package.

The `runtime store` already includes all binaries so the app doesn't have to bring them when publishing 2.0. in and as a result the app is smaller.

Configuration is so important that is now part of ASP.NET Core. It's accessible by DI. Logging is pushed to Whe webHosst now.

+ Razor pages - 
```[TempData]``` annotation for properties. is different from Viewdata. it's intended for 

+ Authentication 

Now it's only app.UseAuthentication() combining middleware like cookies, facebook.. etc. Now with 1 middleware we can't clash and try to do them in the same time like before.

Online Authenticator App [GAuth](http://gauth.apps.gbraad.nl/)

+ Spa Templates - Angular, React React/Redux

When having Angular project we can change things, save the file and webpack monitors for changes and updates the page in the browsers.

+ Performance 

Startup performance compared to 1.1 is going down to 00:00:00.55 from 00:00:03.75 😱
  That's because the pages are precompiled, and the views. Runtime store has all binaries so we save the time to jitter.
  
+ Seamless Diagnostics

Lightup feature - w/o writing a single line of code. Starts AppInsights in Azure

## 3. Diagnostics 101

+ Exclude parts of the code until the problem's found. Exclude whole folders with files that are expected to do something related to the issue we are having.

+ Things to be sceptical of
  + *Your code* - kinda obvious
  + *The debugger's Immediate Window* - better use watches and locals
  + *The debugger's string representation* problem with back slashes in the debugger. Always shows them are \\
  + *Console output (examples: string, floating point)*
  + *Articles from a few months ago* 

## 4. MSBuild

We can change the assembly name in vscode by updating in the `*.csproj` file like so

```xml
<AssemblyName>MyAwesomeProject</AssemblyName>
```

We can add references by using `ItemGroup`'s `Packagereference`

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

We can run gulp with the build

```xml
<Target Name="RunGulp" AfterTargets="Build">
  <Exec Command="node ./node_modules/.bin/gulp compile" />
</Target>
```
 and we will have to run `dotnet restore` and then `dotnet build`

## 5. Visual Studio 2017


The new release 15.5 will be much faster in initial loading. Moved the analysis out of the main VS process which makes a lot faster.

`Live unit testing` is figuring out what changes are done and which lines of code are affected. Before in order to see the tests we had to go to another Window in VS and loose contex and now we can stay in development mode.

Select tests to be in life tests set `Life Unit Test > Include/Exclude`. The beaker icon is empty when excluded.

Add null checks refactoring
![add null checks refacotring](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/add_null_check_refactoring.png)

Ctrl + T doesn't work on my VS2017!!! Not happy

Code style Suggestions `Tools > Options > Text editor > C# > Code style > General` to configure code styling.

The way the editor config works is its applied to everything in the same directory.
![editor config rules](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/editor_config_rules.png)
We can set one rules for the project and completely another for the unit tests.

Mads T has an extension for editor configs. Find it!

**Tuples** in C# 7. They allow us to return different things from methods! we already have them in TypeScript (thank you very much!)

FxCop rules have been used and integrated into Roselyn so that it can give as meaningful suggestions about architecture, design and best practices.

`Ctrl + Click` to go to Definition



## Announcements
.Net Foundation starts sport User groups. They will start Meetup Pro user groups.
![meetup groups](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/meetup_progroup_announcement.png)

## Links
+ .NET Foundation meetups https://dotnetfoundation.org/events
+ Meetup Pro https://www.meetup.com/pro/dotnet/
+ dotnet Presentations https://dotnet-presentations/dotnetcore-workshop
+ questions about .NET standard https://aka/ms/netstandardfaq to Immo Landwerth




# Day 2 Notes

## 1. EF Core 2.0

### Context Pooling. 

![context pooling diagram](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/dbcontext_pooling.png)

Before the context was created per request. Now with context polling the context is served by the pool. We still have 
Connection pooling. Context has a lot of dependencies that it has to load and that slows it down when done per request.
Context Pooling is not by default, it's considered more like Advanced state.

To get to pooling functionality we need to change from `AddDbContext<T>` to `AddDbContextPool<T>`.

![change to context pool](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/add_dbcontext_pool.png)

### Explicit compiled query

Explicittly compiled queries are compiled the first time and cached and then any other time they are used, they are much fatser that regular queries.
EF class has some static entry points.
![explicitly compiled query](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/explicit_compiled_query.png)

### Owned types

![owned types example](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/owned_types_1.png)

If we have `Work Address` and `Physical Address` and we make them as pwned type they get added as a prefixed column name at the parent table

![owned types result table](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnetconf2017/prefixed_column_names.png)

We can also mapped them in the same table. Owned types can be nested. Restriction is that only the parent can point to owned type

### Filters

Interpolated string queries. There is a naive interpolation where even if you put the sql query in a local variable there is still a chance of sql ingection. However if the query is inside of the FromSql method it gets parametrized!

### EF Links 
+ Docs https://docs.microsoft.com/ef/core
+ Project https://github.com/aspnet/EntityFrameworkCore
+ Blog https://blogs.msdn.com/dotnet
+ Demos https://github.com/anpete/efdemos

### Template engine

How to create new template:
  + `dotnet new -h`
  + `dotnet new mvc -h`
  + `dotnet new console -o C9.Demo`
  + `cat Program.cs`
  + `dot net restore && dotnet run`
  + `code .`

The idea is that the current project is the template and we add a folder with config file to describe the templating configs. `Template.Config > template.json`.<br />
`shortname` is the commpand used by the user in the console to create a project with the template.
  + `dotnet new --install`

Links:
  + Official repo https://github.com/dotnet/templating
  + Available templates for `dotnet new` [wiki](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
  + Additional templates aka.ms/dotnet-new-templates
  + dotnet new intro aka.ms/dotnetnew-intro
  + wiki https://github.com/dotnet/templating/wiki
  + samples aka.ms/dotnetnew-template-samples
  + conf samples https://github.com/sayedihashimi/channel9-templates-2017.04.11

## Resource Management

rachardCMS orchards.ResourceManagement NuGet package. Add it to ConfigureServices() with `services.AddResourceManagement()`.<br />
It injects `<script>` tags in the html.

## Library Installer
Easily install client libraries to dotnet project
https://github.com/aspnet/LibraryInstaller

## IIS Administration API

https://github.com/Microsoft/IIS.Administration

## .NET Core for International Users

**Globalization** is the process of building the app so we can work with cultures. Identifying the culture that must be supported. The features have to re written in a way that it behaves the same way in any supported culture.
**Localization** is the process of assigning UI elements with localized text and resizing application's UI elements to accommodate localized text.

  + Globalizing ASP.NET Core 2.0 MVC Projects
  + Resource Files
  + Localizing ASP.NET Core 2.0 MVC Projects
  + User Selectable Culture with Cookies
  + Data Annotations
  + Custom Providers

https://github.com/cwoodruff/DotNetConf2017_i18n
