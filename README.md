
Create a custom template for your organisation standards to ease the project setup by providing the boiler plate code.

1. To create package or template, first step is to create folder '.template.config' under the project.
2. template.json should be added under it. 

```JSON
{
  "$schema": "http://json.schemastore.org/template",
  "author": "surendra Rayapati",
  "classifications": [ "WebAPI", "Swagger", "Application Insights" ],
  "identity": "apitemplate.Template",
  "name": "My Dotnet API Template",
  "shortName": "apitemplate",
  "tags": {
    "language": "C#",
    "type": "project"
  },
  "sourceName": "apitemplate",
  "preferNameDirectory": true,
  "sources": [
    {
      "modifiers": [
        {
          "condition": "(!exclude)",
          "include": "**/*",
          "exclude": [
            "**/[Bb]in/**",
            "**/[Oo]bj/**",
            ".template.config/**/*"
          ]
        }
      ]
    }
  ]
}
```


# Understand above JSON file.

**$schema:** This property specifies the JSON schema that should be used to validate the template.json file. 

**author:** Specifies the author or creator of the template. This is a descriptive field.

**classifications:** An array of strings that categorize the template. These classifications help users find your template when searching or browsing available templates.

**identity:** A unique identifier for the template. This is used internally by the .NET SDK to distinguish between different templates. It should be unique across all templates. A common convention is to use a namespaced identifier.

**name:** The user-friendly name of the template that will be displayed to users when they are creating a new project.

**shortName:** A short, command-line friendly name for the template. Users can use this name with the dotnet new command to create a project from your template (e.g., dotnet new apitemplate).

**tags:** A set of tags that provide additional information about the template.

**language:** Specifies the programming language used by the template (e.g., "C#").

**type:** Specifies the type of template (e.g., "project", "item"). In your case, it's a "project" template, meaning it creates an entire project.

**sourceName:** This property defines the name that will be used to replace tokens within the template's source files. When a user creates a project from the template, any occurrences of sourceName in the files will be replaced with the actual project name provided by the user. This is useful for renaming namespaces, classes, or other identifiers within the project.

**preferNameDirectory:** A boolean value that indicates whether the template should create a new directory with the same name as the project. If set to true, the template engine will create a directory with the project name.

**sources:** An array that describes the source files and how they should be processed.


# create template using below command. (Install template)
dotnet new install .\ 

# To overwrite or replace existing template
dotnet new install <**Project folder root Path>** --force

# Uninstall template using below command.
Navigate to project path and run below command.

dotnet new uninstall <***Project folder root path>**


