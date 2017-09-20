# dotnetconf2017-notes
my notes on www.dotnetconf.com

## 1. Keynote [here](https://github.com/lekova/dotnetconf2017-notes/blob/master/keynote.md)

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
![add null checks refacotring](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/add_null_check_refactoring.png)

Ctrl + T doesn't work on my VS2017!!! Not happy

Code style Suggestions `Tools > Options > Text editor > C# > Code style > General` to configure code styling.

The way the editor config works is its applied to everything in the same directory.
![editor config rules](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/editor_config_rules.png)
We can set one rules for the project and completely another for the unit tests.

Mads T has an extension for editor configs. Find it!

**Tuples** in C# 7. They allow us to return different things from methods! we already have them in TypeScript (thank you very much!)

FxCop rules have been used and integrated into Roselyn so that it can give as meaningful suggestions about architecture, design and best practices.

`Ctrl + Click` to go to Definition



## Announcements
.Net Foundation starts sport User groups. They will start Meetup Pro user groups.
![meetup groups](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/meetup_progroup_announcement.png)

## Links
+ .NET Foundation meetups https://dotnetfoundation.org/events
+ Meetup Pro https://www.meetup.com/pro/dotnet/
+ dotnet Presentations https://dotnet-presentations/dotnetcore-workshop
+ questions about .NET standard https://aka/ms/netstandardfaq to Immo Landwerth
