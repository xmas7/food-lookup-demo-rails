# API v3 Development Environment Setup

A brief introduction about your project goes here.

<br/>

## Prerequisites

Before you begin, ensure you have met the following requirements:

#### 1. You have installed [.NET 7](https://dotnet.microsoft.com/en-us/download/dotnet/7.0)

| OS | Installers |
| ----------- | ----------- |
| Linux | [Package manager instructions](https://learn.microsoft.com/dotnet/core/install/linux?WT.mc_id=dotnet-35129-website) |
| macOS | [Arm64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-macos-arm64-installer) I [x64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-macos-x64-installer) |
| Widnows | [x64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-windows-x64-installer) I [x86](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-windows-x86-installer)|
| All | [dotnet-install scripts](https://dotnet.microsoft.com/en-us/download/dotnet/scripts) |


#### 2. You have installed [Azure Functions Core Tools v4.x](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local)

Azure Functions Core Tools lets you develop and test your functions on your local computer from the command prompt or terminal. Your local functions can connect to live Azure services, and you can debug your functions on your local computer using the full Functions runtime.

>⚠️ Note <br/>
Don't mix local development with portal development in the same function app. When you create and publish functions from a local project, you won't be able to maintain or modify project code in the portal.

<br/>

## Installing & Running Locally

Follow these steps to get your development environment set up and running locally


#### 1. Clone the repository

**Clone the repository using SSH.**
```bash
git clone git@bitbucket.org:prepaidtech/dash-api.git
```
> [Set up personal SSH keys on Windows | Bitbucket Cloud](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-windows/)


**Clone the repository using HTTPS.**
```bash
git clone https://<your-profile-name>@bitbucket.org/prepaidtech/dash-api.git
```

#### 2. Navigate to the project directory

```bash
cd <project-name>
```

#### 3. Install the dependencies

Run below command to restore all the necessary dependencies and packages for the project.

```bash
dotnet restore
```

#### 4. host.json and local.settings.json

A Functions project directory contains the following files and folders, regardless of language:

**host.json** <br/>
The global configuration file host.json includes settings that affect all functions deployed under the same function app.
```bash
{
    "version": "2.0",
    "logging": {
        "applicationInsights": {
            "samplingSettings": {
                "isEnabled": true,
                "excludedTypes": "Request"
            } 
        } 
    } 
}
```

**local.settings.json** <br/>
App settings, connection strings, and settings utilized by local development are all stored in the local.settings.json file. This file is only used when projects are run locally.

```bash
{
    "IsEncrypted": false,
    "Values" : {
        "AzureWebJobsStorage": "UseDevelopmentStorage=true",
        "FUNCTIONS_WORKER_RUNTIME": "dotnet-isolated",
        "MyConnection": "<connection-string-to-your-databse>",
        "MyOptions:Option1": "value",
        "MyOptions:Option2": "value"
    },
    "ConnectionStrings": {
        "DefaultConnection": "UseDevelopmentStorage=true"
    } 
}
```

#### 5. Run the project

We have 5 `.NET Azure Function Apps` in our solution.
```
Dash.Api.Audits.Functions
Dash.Api.Cards.Functions
Dash.Api.Payments.Functions
Dash.Api.Users.Functions
Dash.Api.Webhooks.Functions
```

Navigate to the project directory you want to run. <br/>
Using the following command to Start the Azure Functions runtime host.

```bash
func start
```
<br/> 

If the Function App is running correctly, you can see similar screen on the console.
![Azure Function App](https://drive.google.com/uc?id=1nHXS7dSVVQ-73QhGAfDPI9v8WEtr4OO5)


>⚠️ Note <br/>
Make sure you have [host.json](https://learn.microsoft.com/en-us/azure/azure-functions/functions-host-json) and [local.settings.json](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash#local-settings) files and those are configured properly before running the Function App.

<br/>

## Usage

After starting the function app, you can trigger your function by making a GET or POST request to `http://localhost:7071/api/<YourFunctionName>`.

Replace `<YourFunctionName>` with the name of your function.

<br/>

## Contributing to Project

To contribute to `<Project Name>`, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the original branch: `git push origin <project>/<location>`
5. Create the pull request.

Alternatively see the Bitbucket documentation on [creating a pull request](https://support.atlassian.com/bitbucket-cloud/docs/create-a-pull-request/).

