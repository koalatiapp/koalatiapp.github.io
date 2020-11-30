---
layout: default
title: Formatting results
parent: Tools
nav_order: 50
---

# Formatting results for Koalati
A tool's results are are simply an array of serializable objects. Each of those objects represent a test that the tool has carried out and contains the results for that test.

Here are the properties that are allowed and/or expected for those objects:


| Property          | Required | Allowed types             | Description                                                   |
|-------------------|----------|---------------------------|---------------------------------------------------------------|
| uniqueName        | Yes      | string                    | A slug-like name for the test that is unique within a tool. This will be prefixed with the tool's name to generate a Koalati-wide unique name for the test. |
| title             | Yes      | string                    | A user-friendly title.                                        |
| description       | Yes      | string                    | A user-friendly description of the test.                      |
| weight            | Yes      | float                     | The percentage of your tool's total score that comes from this test. Should be a float between 0 and 1.0 |
| score             | Yes      | float                     | Score obtained by the tested page or website. Should be a float between 0 and 1.0 |
| snippets          | No       | string[], [ElementHandle](https://pptr.dev/#?product=Puppeteer&version=main&show=api-class-elementhandle)[] | A list of strings to represent as code snippets in Koalati's results. |
| table             | No       | array[]                   | A two-dimensional array of data that will be represented as a table in Koalati's results. The first row should contain the column's headings. |
| recommendations   | No       | string, string[]          | Recommendation(s) telling the user what can be done to improve their results |
