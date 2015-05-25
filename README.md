orionx-cli
======

> Console scaffolding and development tool for Meteor Apps.
> Cutting edge fork


## How to install

```bash
npm install -g orionx-cli
```
    
## How to use

### Creating apps

You can create meteor apps by using __orionx create__, which downloads the [Meteor Boilerplate](https://github.com/matteodem/meteor-boilerplate).
__--blank__ or __-b__ let's you create a blank app (same as calling ```orionx init```). 

```bash
orionx create meteorApp
orionx create -b blankApp
```

If you have a proxy, you need to set the ``http_proxy`` variable to access the repository.

```bash
export http_proxy=http://myproxy.net:myport
```

### Reset apps

You can reset the app to remove all the default code.

```bash
orionx init
```

### Initializing exiting apps

Initialize Meteor Apps for use with scaffolding with following command.

```bash
cd existingMeteorApp
orionx init
```

The resulting file orion-config.json under private/ has existing templates, list them by calling ```orionx generate```. The configuration has following
structure.

```json
{
    "generate" : {
        "templateName" : {
            "default" : {
                "desc" : "description for template",
                "files" : ["private/templates/someFile.html"],
                "variables" : [
                    {
                        "name" : "templateVar",
                        "desc" : "templateQuestion"
                    }
                ]
            },
            "otherProfileName" : {
                "files" : ["private/templates/someOtherFile.html"]
            }
        }
    }
}
```

The template file also has one required line of configuration, which looks like following.

```html
<!-- { "path" : "client/views/__templateVar__.html" } -->
<template name="__templateVar__">
    <h1>This is the content</h1>
<template>
```

You can use the variables in the template, as long as the json configuration for the path is on the first line it'll recognize it.

### Generating files

You can create views, routes, models and more in the default configuration or change it and add more templates.

```bash
orionx generate [entity] [name] [param]
```

Example:

```bash
orionx generate view
orionx generate routes
```

Advanced usage:

```bash
orionx generate view name-of-view
orionx generate routes category /category/:id
```

### Change profiles

The default profiles in the configuration are __es6__ and __coffee__, which generates other kind of files. You can also define your own profiles.

```bash
orionx set-profile coffee
```
