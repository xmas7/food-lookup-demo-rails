# API v3 Development Environment Setup

A brief introduction about your project goes here.

# Prerequisites

Before you begin, ensure you have met the following requirements:

- You have installed [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- You have installed [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local)
- You have a basic understanding of C# or the programming language used in this project

# Installing & Running Locally

Follow these steps to get your development environment set up:

## Clone the repository

```bash
git clone https://jordanfrazier@bitbucket.org/prepaidtech/dash-api.git
```
```bash
git clone git@bitbucket.org:prepaidtech/dash-api.git
```


## Navigate to the project directory

```bash
cd <project-name>
```

3. **Install the dependencies**

Make sure to restore any dependencies for your project. If it's a .NET project, you can use the following command:

```bash
dotnet restore
```

4. **Run the project**

Start the Azure Functions runtime host using the following command:

```bash
func start
```

## Usage

After starting the function app, you can trigger your function by making a GET or POST request to `http://localhost:7071/api/<YourFunctionName>`.

Replace `<YourFunctionName>` with the name of your function.

## Contributing to Project

To contribute to `<Project Name>`, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the original branch: `git push origin <project>/<location>`
5. Create the pull request.

Alternatively see the GitHub documentation on [creating a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).


# H1
## H2
### H3
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
> This is the first line of the blockquote.
> This is the second line of the blockquote.
