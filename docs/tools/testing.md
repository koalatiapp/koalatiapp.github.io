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

## Unit/functional testing
The [tool template](https://github.com/koalatiapp/tool-template) comes with a basic testing setup, which uses [`mocha`](https://mochajs.org/), [Node's `assert`](https://nodejs.org/api/assert.html) and the [`@koalati/dev-tool-tester`'s `runTool`](https://github.com/koalatiapp/dev-tool-tester) function.

You can run your tool's tests by running the following command:
```bash
npm test
```

The `runTool` function is the most important aspect of it all, as it provides all of the dependencies and logic required to run your tool on a webpage (or local file). All you have to manage is the validation of the results. You can find more information about it in the [`@koalati/dev-tool-tester`](https://github.com/koalatiapp/dev-tool-tester)'s repository.

The tests are found in the `test` directory of this template. It contains three files you'll most likely want to update or expand upon in your own tool:
- `/test/sample.html`: a simple HTML file on which your tool will be ran for the test's purpose.
- `/test/expectation.json`: a JSON containing the results that are expected to come out of your tool when it is ran on the `/test/sample.html` page.
- `/test/index.js`: the actual script that defines and executes the tests.

### Testing framework
Although `mocha` is bundled in with the tool template by default, you are free to use any testing framework you like: there is no limitations when it comes to dev dependencies.