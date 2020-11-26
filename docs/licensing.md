---
layout: default
title: Licensing
nav_order: 60
---

# Licensing

Every open-source project or library that is developed at Koalati is distributed by an [MIT license](https://github.com/koalatiapp/koalatiapp.github.io/blob/master/LICENSE){: target="_blank"}.

When you contribute to Koalati's repositories, it is essential that you do not copy or reuse code from non-MIT licensed sources.

## External librairies

Every library used by Koalati's projects and librairies are considered external, as they are linked dynamically. Therefore, any library or tool you develop and integrate into Koalati is considered an external library for Koalati's licensing purposes.

External librairies used by Koalati can be distributed under any open-source license of your choice, although we strongly recommend using an MIT license.

If you have any question about open-source licensing, or if you need help picking a license, please refer to the [Open Source Initiative's website](https://opensource.org/licenses){: target="_blank"}

### Vendor libraries

To ensure that you respect the license, and as a general good practice for any project, make sure that your vendor librairies are not included directly into your library's source code.

This can usually be achieved by ignoring the vendor libraries folder (such as `node_modules` for Node projects, or `vendor` for PHP projects) in your `.gitignore` file.
