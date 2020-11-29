---
layout: default
title: Testing your tools
parent: Tools
nav_order: 40
---

# Testing your tools
When working on a tool, it is essential to test it to ensure that it works as expected.

Below, you'll learn how to run your tool from the command line. You will also learn to set up unit test for your tools. Let's get started.

## Running your tool from the CLI
You can test your tool from the CLI by using the [@koalati/dev-tool-tester](https://github.com/koalatiapp/dev-tool-tester){: target="_blank"}.

To do so, simply navigate to your tool's directory and use the following command:
```bash
npx @koalati/dev-tool-tester --url="https://www.your-website-url.com/"
```

In addition to running your tool and returning the results, the [@koalati/dev-tool-tester](https://github.com/koalatiapp/dev-tool-tester){: target="_blank"} package also validates the format of your tool's results.

If an error occcured while running your tool, or if your tool's results don't match the expected format, an error will appear in your CLI.

Otherwise, a success message followed by the JSON-encoded results will be displayed.


## Results format validation
In order to make use of a tool's results, Koalati requires that they follow a specific structure/format.

This format will be validated by the [@koalati/dev-tool-tester](https://github.com/koalatiapp/dev-tool-tester){: target="_blank"} when you run your tool from the CLI, so you can easily find incompatibilities and fix them before publishing your tool.

It is essential that your tool respects Koalati's format, otherwise it will not be accepted when you will attempt to publish it.

To avoid that from happening to you, take a look at our section documenting the exact format that is expected from all Koalati tools.

[View the Results format and validation section](/docs/tools/formatting-results){: .btn .btn-purple }

## Unit testing
Coming soon
{: .label .label-yellow }
