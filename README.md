# API v3 Development Environment Setup
Instructions on setting up and running the v3 APIs locally.

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

#### 3. Local storage emulator [Azurite](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azurite)
During local development, you can use the local [Azurite emulator](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azurite) when testing functions with Azure Storage bindings, without having to connect to remote storage services. Azurite integrates with Visual Studio Code and Visual Studio, and you can also run it from the command prompt using npm. For more information, see [Use the Azurite emulator for local Azure Storage development.](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azurite)
<br/>

The following setting in the Values collection of the local.settings.json file tells the local Functions host to use Azurite for the default AzureWebJobsStorage connection:
```JSON
"AzureWebJobsStorage": "UseDevelopmentStorage=true"
```

## Installing & Running
Follow these steps to get your development environment set up and running locally


#### 1. Clone the repository

*Clone the repository using SSH.*
```bash
git clone git@bitbucket.org:prepaidtech/dash-api.git
```
> Set up personal [SSH keys](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-windows/) on Windows | Bitbucket Cloud


*Clone the repository using HTTPS.*
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

#### 4. Configuration Files
A Functions project directory contains the following files and folders, regardless of language:

***`local.settings.json`*** <br/>
Settings used by Core Tools when running locally, including app settings. To learn more, see [local settings.](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash#local-settings)

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

***`host.json`*** <br/>
The global configuration file host.json includes settings that affect all functions deployed under the same function app. To learn more, see the [host.json reference.](https://learn.microsoft.com/en-us/azure/azure-functions/functions-host-json)

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


#### 5. Run the project
We have `5 .NET Azure Function Apps` in our solution.

>Dash.Api.Audits.Functions <br/>
Dash.Api.Cards.Functions <br/>
Dash.Api.Payments.Functions <br/>
Dash.Api.Users.Functions <br/>
Dash.Api.Webhooks.Functions

Navigate to the project directory you want it to be running. <br/>
Using the following command to Start the Azure Functions runtime host.

```bash
func start
```

>⚠️ Note <br/>
Make sure you have [host.json](https://learn.microsoft.com/en-us/azure/azure-functions/functions-host-json) and [local.settings.json](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash#local-settings) files and those are configured properly before running the Function App.

<br/> 

If the Function App is running correctly, you can see similar screen on the console.
<img src="https://drive.google.com/uc?id=1nHXS7dSVVQ-73QhGAfDPI9v8WEtr4OO5" alt="Azure Function App">


## Test with [Postman](https://www.postman.com/)
Postman is a standalone software testing API platform to build, test, design, modify, and document APIs.

You can see OpenAPI definitions here for Function Apps.
```
dash-api\Dash.Terraform\modules
```
Once you have `Function App` up and running, you can import the OpenAPI definitions into Postman to test them out. <br/>

e.g. Dash Cards API
```
dash-api\Dash.Terraform\modules\cards-service\open-api-cards.yaml
```

<img src="https://drive.google.com/uc?id=13RKGzRgOYPKoMxqNdaPuRNT2BudPlN1z" alt="Postman Collection">

<br/>

>⚠️ Note <br/>
Make sure you are using [Postman Desktop Agent](https://learning.postman.com/docs/getting-started/installation-and-updates/#installing-the-postman-desktop-agent)

## Contributing to Project
To contribute to `<Project Name>`, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the original branch: `git push origin <project>/<location>`
5. Create the pull request.

Alternatively see the Bitbucket documentation on [creating a pull request](https://support.atlassian.com/bitbucket-cloud/docs/create-a-pull-request/).
