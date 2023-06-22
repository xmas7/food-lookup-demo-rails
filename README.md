# API v3 Development Environment Setup

A brief introduction about your project goes here.


# Prerequisites

Before you begin, ensure you have met the following requirements:

## You have installed [.NET 7](https://dotnet.microsoft.com/en-us/download/dotnet/7.0)

| OS | Installers |
| ----------- | ----------- |
| Linux | [Package manager instructions](https://learn.microsoft.com/dotnet/core/install/linux?WT.mc_id=dotnet-35129-website) |
| macOS | [Arm64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-macos-arm64-installer) I [x64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-macos-x64-installer) |
| Widnows | [x64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-windows-x64-installer) I [x86](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.304-windows-x86-installer)|
| All | [dotnet-install scripts](https://dotnet.microsoft.com/en-us/download/dotnet/scripts) |


## You have installed [Azure Functions Core Tools v4.x](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local)

Azure Functions Core Tools lets you develop and test your functions on your local computer from the command prompt or terminal. Your local functions can connect to live Azure services, and you can debug your functions on your local computer using the full Functions runtime.

>⚠️ Note <br/>
Don't mix local development with portal development in the same function app. When you create and publish functions from a local project, you won't be able to maintain or modify project code in the portal.




# Installing & Running Locally

Follow these steps to get your development environment set up and running locally

## 1. Clone the repository

```bash
git clone https://jordanfrazier@bitbucket.org/prepaidtech/dash-api.git
```
```bash
git clone git@bitbucket.org:prepaidtech/dash-api.git
```


## 2. Navigate to the project directory

```bash
cd <project-name>
```

## 3. Install the dependencies

Make sure to restore any dependencies for your project. If it's a .NET project, you can use the following command:

```bash
dotnet restore
```

## 4. Run the project

Start the Azure Functions runtime host using the following command:

```bash
func start
```

# Usage

After starting the function app, you can trigger your function by making a GET or POST request to `http://localhost:7071/api/<YourFunctionName>`.

Replace `<YourFunctionName>` with the name of your function.

# Contributing to Project

To contribute to `<Project Name>`, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the original branch: `git push origin <project>/<location>`
5. Create the pull request.

Alternatively see the GitHub documentation on [creating a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).


**bold text**
*italicized text*
> blockquote
1. First item
2. Second item
3. Third item
- First item
- Second item
- Third item
`code`
---
    [title](https://www.example.com)

![alt text](image.jpg)


| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

### My Great Heading {#custom-id}


term
: definition

~~The world is flat.~~


- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media


That is so funny! :joy:

I need to highlight these ==very important words==.

H~2~O

X^2^


> :warning: **WARNING:** Be careful with this.



**⚠️ WARNING: Be careful with this.**


> This is the first line of the blockquote.
> This is the second line of the blockquote.
> This is the first line of the blockquote.
> This is the second line of the blockquote.
