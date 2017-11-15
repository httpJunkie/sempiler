---
layout : feature
video : qAnwW0O7Dkk
title : VSC Ext
since : 0.1
targets : [C++, Swift]
---

The Sempiler extension is available from the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/search?term=sempiler&target=VSCode&category=All%20categories&sortBy=Relevance).

## <a name="languages"></a>Languages

### <a name="typescript"></a>TypeScript

The current extension is based on the **assumption** that a lot of Visual Studio Code users are comfortable with TypeScript as their chosen source language.

Additional source languages may come later based on community appetite for them.

### <a name="targets"></a>Targets

Details about the current set of target platforms can be found [here](../latest#targets).

## <a name="workspace"></a>Workspace

Sempiler will configure your workspace automatically as soon as it detects a project with a [config file](#sempiler-config) at the root. 

You can call the [Init task](#tasks) to **create this file automatically**.

### <a name="sempiler-config"></a>Sempiler Config

The `semconfig` file is a standard JSON file that lives at the **workspace root**. It can be created at any time by running the [Init task](#tasks).

The extension delegates to the Sempiler application under the hood (it is not coupled with Visual Studio Code). We use the sem config file to set some of the options:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `inputPath : string` | Input source file path or directory containing input source files | All source files must be children of this path, except for stub APIs |
| `outputDirPath : string` | Output directory for emitted artifacts | Does not need to be inside workspace root |
| `target : string` | Name of the target platform | Check extension README for platform names your installed version supports |
| `compileOnSave? : boolean` | Run sempiler every time an input source file is saved |  |
| `postCmd? : string` | Command to execute after successful sempilation | Executed on command line |
| `beautifyOutput? : boolean` | Beautify the output files | Only works in C++ for now. Swift can be done via postCmd using 'swiftformat' |

If you are sempiling code to contribute to an project that is being **maintained natively in parallel**, your `outputDirPath` could point to that project's location whilst keeping your sempiler workspace **separate** from it.

### <a name="env-vars"></a>Env Vars

Configuration settings like `postCmd` support a limited set of environment variable substitutions.

Along with any of the symbols from the [`semconfig`](#sempiler-config), you can also get session diagnostics:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `duration : number` | How long Sempiler took to run in milliseconds | |
| `outputPaths? : string` | Command to execute after successful sempilation | Single space delimited list of all file paths written  |

### <a name="sempiler-modules"></a>Sempiler Modules

The `sem_modules` directory lives at the **workspace root**. This is where the extension looks for [stub APIs](stub-apis). It can be created at any time by running the [Init task](#tasks).

You can add definitions and [packages](#packages) to this folder as and when required during the development of your project. 

The `sem_modules` directory **should** be version controlled, and **should not** be confused with the convention of git ignoring the `node_modules` directory.

### <a name="sem-prefix"></a>@sem prefix

For now the extension expects any imports of [stub APIs](stub-apis) to be prefixed with `@sem/` in the path.

This will direct the module resolver to search in the [sem_modules directory](#sempiler-modules) for a matching relative path.

<script src="https://gist.github.com/ComethTheNerd/66bc14697f17f347db3c9fd7d3870c58.js"> </script>

This convention is also useful for collaborators to easily determine at a glance which dependencies are **purely symbolic**.

### <a name="ts-config"></a>TS Config

The `tsconfig` file is **managed automatically** by the extension. Any manual edits will be overwritten by the extension, or could conflict with it's operation.

The extension specifically writes the `tsconfig` to ensure a developing experience that is as smooth as possible. It is used purely as an interface to the influence the TypeScript compiler and Intellisense in the editor.

You may wish to `.gitignore` the `tsconfig` when working in a team and/or on multiple computers.

### <a name="intellisense"></a>Intellisense

If everything is setup correctly, you should find that the extension feeds back any Sempiler errors to you as you live code in the Visual Studio Code editor. These will be **underlined in red**, along with an accompanying tool tip.

Sempiler will only catch some violations of **target semantics**. It mostly leaves this to the target compiler, with the exception of easy to detect issues that give the developer **fast feedback**.

For example, failing to unwrap optionals (Swift) or writing code that cannot be compiled in a single pass (C++).

<aside>
Sempiler also reports TypeScript diagnostics
</aside>

## <a name="tasks"></a>Tasks

Upon activation the extension will register the following tasks that you can find in the Visual Studio Code tasks menu:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `Sempiler : Init` | Setup your workspace for sempiling | Creates a [`semconfig`](#sempiler-config) with default properties that you may want to edit |
| `Sempiler : Run` | Run sempiler | This will emit artifacts based on your [`semconfig`](#sempiler-config) file |

## <a name="packages"></a>Packages

At present there is no dedicated way of importing packages for your Sempiler project. It is sufficent to use the standard `package.json` to load dependencies, providing their implementation is compatible with the target platform you are sempiling to, and the [current features](../latest) supported by your version of Sempiler.

## <a name="issues"></a>Issues

Please consult the [guidelines](../latest#issues) for advice on how best to communicate any issues.