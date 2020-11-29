---
layout: default
title: Tool basics
parent: Tools
nav_order: 20
---

# Tool basics

Tools are imported as any other regular NPM dependency, via the `require()` function. They are executed once the target webpage has already been successfully loaded by a headless Chromium browser via Puppeteer.

A tool's flow consists of four basic phases:
- [Initialization](#initialization)
- [Execution](#execution)
- [Results formatting](#results-formatting)
- [Clean up](#clean-up)

Each of these phase is represented by a method in the tool's class. Let's dive into each of these in more details.

## Initialization
`constructor()`

A tool's Initialization phase takes place in the its constructor. This is where most of the configuration and early preparations should be done.

When a tool is initialized, an object is provided to its constructor, providing the following data:

| Key             | Description            |
|-----------------|------------------------|
| page            | A Puppeteer [`Page`](https://pptr.dev/#?product=Puppeteer&version=main&show=api-class-page) instance in incognito mode, with the target URL already loaded. |
| consoleMessages | An object containing every message that has been outputted to the browser's consoles for this page, grouped by type. Each of the following keys contains an array of messages: `errors`, `warnings`, `others` |
| devices         | A copy of [`puppeteer.devices`](https://pptr.dev/#?product=Puppeteer&version=main&show=api-puppeteerdevices), which is a list of devices to be used with `page.emulate(options)`. |

If you don't use all of these options, it is a good practice to only assign the ones you do. This can be done quite easily with object destructuring.

Here is an example of a tool that only uses the `page` object:

```js
class Tool {
    constructor({ page }) {
        this.page = page;
    }

    // ...
}
```

## Execution
`async run()`

The execution phase is where all of the heavy lifting and processing happens for your tool.

For simple tools, the content of this method may be something as simple as checking if an element exists on a page.

However, for more complicated tools, it is recommended to split your execution code into multiple methods and/or classes, and to simply initiate the execution in the `run()` method.

The `run()` method is not expected to return anything. Instead, the results of your tools should be kept in a property within your tool, as they are expected to be formatted and accessed in the `results` getter method.


## Results formatting
`get results()`

The results formatting phase takes place within the `results()` getter method.

In this method, you should use the previously obtained results from your tools to return a formatted array of objects.
This getter method should contain little to no logic or processing: it's only goal is to return the results in the Koalati's desired format

To learn more about the Koalati results format, check out our section on the subject.

[View the Results format and validation section](/docs/tools/formatting-results){: .btn .btn-purple }


## Clean up
`async cleanup()`

In this phase, you should clean up any variable, API connection, DOM modification, and any other changes your tool's execution has done during its intialization, execution and formatting phases.

This method will only be called once your tool has been executed and its results have been collected, right before the tool's instance is discarded.

Your goal here is to put everything back the way it was before your tool was initialized.

If your tool is inherently "destructive", meaning that it alters the DOM or the Puppeteer page in a way that cannot be restored, it's okay: simply make sure to indicate this behaviour when submitting your tool for publication.
