# Keynote

Starting with `dotnet cli`

1. How to check and change the version of dotnet core for a specific project. It can be done by changing the SDK version in the `global.json`.

![change SDL version](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/change_dotnet_skd_for_a_project.png)

2. Add existing projects as a reference by using ```dotnet add reference...```

![add project as a reference](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnet_core_cli_add_existing_project.png)

3. When a project is created in the command line it doesn't have the sln file. If we want to work with VS we can create sln file and add the project to it

use `dotnet new sln` to create `sln` file inside the project folder

![create sln](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnet_core_cli_to_open_proj_in_vs__create_sln-_ile.png)

use `dotnet sln add <your project>.csproj` to add the project to the solution

![add project to the solution](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dotnet_core_cli_add_things_to_sln.png)

5. In C# 7.1 Main method can be made async 

![async main method](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/main_methods_now_can_return_tasks_to_be_async.png)

6. Mono and WebAssembly - to research here https://github.com/lrz/mono-wasm

![mono and webassembly](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/expose_csharp_to_the_browser.png)
