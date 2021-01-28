---
layout: default
title: Getting started
nav_order: 20
---

# Getting started

## Prerequisites
To create a new tool or contribute to an existing one, you will need the know or learn the following:
- Git basics <i class="text-grey-dk-000">(to clone a base repository and submit your contributions)</i>
- GitHub basics <i class="text-grey-dk-000">(to submit issues and pull requests)</i>
- Javascript
- Node.js and NPM basics <i class="text-grey-dk-000">(to manage packages and dependencies)</i>

## Dependencies
Koalati tools are built with [Node.js](https://nodejs.org/), a JavaScript runtime built on Chrome's V8 JavaScript engine. View the [Node.js Quick Start guide](https://nodejs.dev/learn/how-to-install-nodejs) for more information about the download and installation process.

Other dependencies might be required depending on the tool you are creating or contributing to.
Please refer to that project's repository for more detailed information.

## Quick start
In just a few minutes, the following steps will get set up to build a new tool or contribute to an existing one.

1. Clone your desired repository.
    - **If you are building a new tool**, use our [Tool Template repository](https://github.com/koalatiapp/tool-template) as a starting point.
    ```bash
    git clone https://github.com/koalatiapp/tool-template.git
    ```
    - **If you are contributing to an existing tool**, clone the tool's repository from [Koalati's GitHub](https://github.com/koalatiapp/).
    Here is an example with Koalati's Social Tool:
    ```bash
    git clone https://github.com/koalatiapp/tool-social.git
    ```
2. Navigate to your newly cloned directory.
```bash
cd your-tool-directory-here
```

3. Install the tool's dependencies via NPM by running the following command:
```bash
npm install
```

    Koalati tools are based on [Puppeteer](https://github.com/puppeteer/puppeteer){: target="_blank" .text-grey-dk-100 }, which installs and uses the Chromium browser. Contributors who work on many Koalati tools might prefer to only download and install one instance of Puppeteer and Chromium to use with every tool in order to save storage space. For more information about how to do this, [view this StackOverflow post on the subject](https://stackoverflow.com/questions/15636367/nodejs-require-a-global-module-package){: target="_blank" .text-grey-dk-100 }.
    {: .fs-2 .text-grey-dk-000 }

4. Make the desired changes and/or additions to the tool's source code. For more information about how Koalati tools work and are structured, [view the Tools section](/docs/tools).

5. Run your tool from the CLI using one of the two following commands. If no error occurred, JSON results should be returned and displayed in your CLI. Otherwise, the error's information will appear.
    - Run your tool on Koalati's homepage like such:
    ```bash
    npm run debug
    ```
    - Run your tool on the URL of your choice by running the [@koalati/dev-tool-tester](https://github.com/koalatiapp/dev-tool-tester) script, as such:
    ```bash
    npx @koalati/dev-tool-tester --url="https://www.your-website-url.com/"
    ```

## Publishing your contributions
Once your development is complete, visit the [Contributing section](/docs/contributing) to learn how to get your tool published and used in Koalati.

## Support
If you encounter problems while creating a tool or contributing to an existing one, feel free to reach out at [info@koalati.com](mailto:info@koalati.com) or to submit an issue on GitHub.
