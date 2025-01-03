# TypeSpec Extension for Visual Studio Code

## Test Environment

* OS : Windows or Linux
* Language : Python, Java, JavasSript, .NET

> Note: The extension should support all test cases in VS Code for Windows and Linux. Mac support is a stretch goal for Selenium semester.

## Prerequisites

Install TypeSpec Compiler before starting to write TypeSpec.

* Node.js 20 LTS or above
* Npm 7+
* Install TypeSpec Compiler CLI: `"npm install -g @typespec/compiler"`

## Test Cases

The TypeSpec Extension aims to provide end-to-end TypeSpec support for non-branded services, covering the following test cases:

* Install the typespec extension
* Create TypeSpec Project
* Generate Client Code from TypeSpec
* Generate OpenAPI 3.x from TypeSpec
* Generate Server Stub from TypeSpec

## Test Steps

### Typespec expansion on Windows

#### Test Cases 1: Install the typespec extension

**Option 1**. Install using .vsix file.
   `Extension` -> `…` -> `Install form VSIX...`
   
   ![alt text](./image/InstallTypespec_VSIX.png)

   Find the .vsix file you want to install locally.
   
   ![alt text](./image/InstallTypespec_SelectVSIXFile.png)

**Option 2**. Install typespec with vscode extension marketplace.
   `Extension` -> input `typespec` -> Install
   
   ![alt text](./image/InstallTypespec_ExtensionMarketplace.png)

#### Test Cases 2: Create TypeSpec Project

New TypeSpec projects can be created using a variety of templates for specific purposes. TypeSpec supports the following non-branded templates:

* Empty Project
* Generic REST API
* TypeSpec Library (with TypeScript)
* TypeSpec Emitter (with TypeScript)

Selecting a template involves:

* Installing required libraries
* Initializing essential project files with a specified folder structure
* Configuring output settings for a designated emission purpose

##### Trigger create TypeSpec Project

**Option 1**. Clicking “Create TypeSpec Project” button/link in the “No Folder Opened” View of Explore.
   
   ![alt text](./image/TriggerCreateTypeSpecProject_NoFolderOpened.png)

**Option 2**. Typing `> TypeSpec: Create TypeSpec Project` in the _Command Palette_.
   
   ![alt text](./image/TriggerCreateTypeSpecProject_CommandPalette.png)

##### Create TypeSpec Project Steps

1. Typing `>TypeSpec: Create TypeSpec Project` in the _Command Palette_.

   **Validate:** It should display the corresponding commands `>TypeSpec: Create TypeSpec Project`.
   
   ![alt text](./image/TriggerCreateTypeSpecProject_CommandPalette.png)

2. Select an empty folder as the root folder for the new TypeSpec project.
   
   ![alt text](./image/CreateTypeSpecProject_SelectFolder.png)

3. If the TypeSpec Compiler is not installed, the Quick Pick will initiate the installation of the TypeSpec Compiler. If TypeSpec Compiler is installed, Skip to the next step.
   
   ![alt text](./image/CreateTypeSpecProject_InstallTypeSpecCompiler.png)

4. After successfully installing TypeSpec Compiler, will go through the questions of `tsp init`.
   1. If the specified folder is not empty. If the folder is empty, skip to the next step.

     **Validate:** Will it appear: `Folder C:\xxx\xxx\xxx is not empty. Are you sure you want to initialize a new project here?`

   2. Select a template.

   **Validate:** There should be a prompt "Select a template", and should see four options: `Empty project`, `Generic REST API`, `TypeSpec Library (With TypeScript)`, `TypeSpec Emitter (With TypeScript)`.

   3. Input project name.

   4. Choose whether to generate a .ignore file. `Y/N`

#### Test Cases 3: Generate Client Code from TypeSpec

Generate client code from TypeSpec. In VS Code extension, we can complete code generation with step-by-step guidance.  
TypeSpec Extension support will be extended to client code generation for first-class languages: `.NET`, `Python`, `Java`, and `JavaScript`.

##### Install the required tools when Generate Client Code

* Install required SDK/runtime for executing the specified language
* .NET 8.0 SDK or above
* Java 11 or above, and Maven
* Python 3.8 or above
* Node.js 20 LTS or above

##### Trigger generate from TypeSpec

Generation from a TypeSpec can be triggered in two ways:

**Option 1**. Clicking `Generate from TypeSpec` in the _Context Menu_ for a .tsp file in the extended TypeSpec project.
   
   ![alt text](./image/TriggerGeneratefromTypeSpec_ContextMenu.png)

**Option 2**. Typing `>TypeSpec: Generate from TypeSpec` in the _Command Palette_ with at least a TypeSpec project folder extended in the _Side Bar_.
   
   ![alt text](./image/TriggerGeneratefromTypeSpec_CommandPalette.png)

##### Generate Client Code steps

1. Input `> TypeSpec: Generate from Typespec`.

   **Validate:** It should display the corresponding commands `TypeSpec: Generate from Typespec`.

   ![alt text](./image/TriggerGeneratefromTypeSpec_CommandPalette.png)

2. Click the command `TypeSpec: Generate from TypeSpec`, and choose a project.

   **Validate:** There should be a prompt "Select a Typespec Project".

   ![alt text](./image/GeneratefromTypeSpec_SelectTypespecProject.png)

3. Select an Emitter Type.

   **Validate:** There should be a prompt "Select an Emitter Type", and should see three emitter types: `Client Code`, `<PREVIEW> Server Stub`, `Protocal Schema`.

   ![alt text](./image/GeneratefromTypeSpec_SelectEmitter_client.png)

4. Click `Client Code`.

   **Validate:** There should be a prompt "Select a Language", and should see four languages: `DotNet`, `Java`, `JavaScript`, `Python`.

   ![alt text](./image/GeneratefromTypeSpec_SelectClientLanguage.png)

5. Select a Language, the TypeSpec to client code generation is initiated at the back end.

   **Validate:** The result appears as a Notification in the bottom right corner, and generate the client folder.

   ![alt text](./image/GeneratefromTypeSpec_GenerateClientResult_prompt.png)
   ![alt text](./image/GeneratefromTypeSpec_GenerateClientResult_Folder.png)

#### Test Cases 4: Generate OpenAPI 3.x from TypeSpec

Emit OpenAPI3 from TypeSpec to automate API-related tasks: generate API documentation, test API, etc.
The TypeSpec file itself is not sufficient to generate OpenAPI 3. The conversion process will always reference the entry point (main.tsp) of the TypeSpec build, which includes the main definitions of models, services, and operations.

##### Generate OpenAPI 3.x steps

1. Input `>TypeSpec: Generate from Typespec`.

   **Validate:** It should display the corresponding commands `TypeSpec: Generate from Typespec`.

   ![alt text](./image/TriggerGeneratefromTypeSpec_CommandPalette.png)

2. Click the command `TypeSpec: Generate from TypeSpec`, and choose a project.

   **Validate:** There should be a prompt "Select a Typespec Project".

   ![alt text](./image/GeneratefromTypeSpec_SelectTypespecProject.png)

3. Select an Emitter Type.

   **Validate:** There should be a prompt "Select an Emitter Type", and should see three emitter types: `Client Code`, `<PREVIEW> Server Stub`, `Protocal Schema`.

   ![alt text](./image/GeneratefromTypeSpec_SelectEmitter_OpenAPI.png)

4. Click `Protocal Schema`.

   **Validate:** There should be a prompt "Select a Language", and should see languages: `OpenAPI3`.

   ![alt text](./image/GeneratefromTypeSpec_SelectOpenAPILanguage.png)

5. Select a Language, the TypeSpec to OpenAPI generation is initiated at the back end.

   **Validate:** The result appears as a Notification in the bottom right corner, and generate the schema folder.

   ![alt text](./image/GeneratefromTypeSpec_GenerateOpenAPIResult_prompt.png)
   ![alt text](./image/GeneratefromTypeSpec_GenerateOpenAPIResult_Folder.png)

#### Test Cases 5: Generate Server Stub from TypeSpec

The service stub generation support will be PREVIEWED for 2 languages: `.NET` and `JavaScript`.
> Note: Server Stub Emitter is currently under PREVIEW.

##### Generate Server Stub steps

1. Input `>TypeSpec: Generate from Typespec`.

   **Validate:** It should display the corresponding commands `TypeSpec: Generate from Typespec`.
   
   ![alt text](./image/TriggerGeneratefromTypeSpec_CommandPalette.png)

2. Click the command `TypeSpec: Generate from TypeSpec`, and choose a project.

   **Validate:** There should be a prompt "Select a Typespec Project".

   ![alt text](./image/GeneratefromTypeSpec_SelectTypespecProject.png)

3. Select an Emitter Type.

   **Validate:** There should be a prompt "Select an Emitter Type", and should see three emitter types: `Client Code`, `<PREVIEW> Server Stub`, `Protocal Schema`.

   ![alt text](./image/GeneratefromTypeSpec_SelectEmitter_ServerStub.png)

4. Click `<PREVIEW> Server Stub`.

   **Validate:** There should be a prompt "Select a Language", and should see two languages: `DotNet`, `JavaScript`.

   ![alt text](./image/GeneratefromTypeSpec_SelectServerStubLanguage.png)

5. Select a Language, the TypeSpec to Server Stub generation is initiated at the back end.

   **Validate:** The result appears as a Notification in the bottom right corner, and generate the server folder.

   ![alt text](./image/GeneratefromTypeSpec_GenerateServerStubResult_prompt.png)
   ![alt text](./image/GeneratefromTypeSpec_GenerateServerStubResult_Folder.png)

## Issue Report

When an error is detected, it’s necessary to document the findings by using the following form:

| Title | Emitter Type | Language | Issue Description | Repro Steps | Expected Results | Actual Results | Comments |
|  --------------- | :-: | :--: | :--: | :--: | :--: | :--: | :--: |
| e.g. Generate client code from typespec failed | client code | Python |  |  |  |  | Issue link |
| e.g. Create typespec project failed | N/N | N/N | Create project feature is not supported by the current TypeSpec Compiler (ver <= 0.63.0). Please upgrade TypeSpec Compiler and try again. | 1. Typing `>TypeSpec: Create TypeSpec Project` in the _Command Palette_. <br> 2. Select an empty folder as the root folder for the new TypeSpec project. <br> 3. Select a template. | There should be a prompt "Select a template", and should see four options: `Empty project`, `Generic REST API`, `TypeSpec Library (With TypeScript)`, `TypeSpec Emitter (With TypeScript)`. | Create project feature is not supported by the current TypeSpec Compiler (ver <= 0.63.0). Please upgrade TypeSpec Compiler and try again. | Issue link |

## Test Results Summary

The test results will be presented in the following form:

| NO | Test Cases | Language | Result | Issues | Status | Comments |
|  --------------- | :-: | :--: | :--: | :--: | :--: | :--: |
| 1 | Install the typespec extension | N/N | PASS | No issue | Done |  |
| 2 | Create TypeSpec Project | N/N | FAIL | Issue links | Done |  |
| 3 | Generate Client Code from TypeSpec | Python | PASS | No issue | Done |  |
| 4 |  | Java | FAIL | Issue links | Done |  |
| 5 |  | .NET | FAIL | Issue links | Done |  |
| 6 |  | JavaScript | PASS | No issue | Done |  |
| 7 | Generate Server Stub steps | DotNet |  |  | Doing |  |
