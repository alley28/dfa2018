---
title: manualoverride
toc: false
sidebar: labs_sidebar
folder: master
permalink: /manualoverride.html
summary: api docs
applies_to: [developer,administrator,consumer]
---
In order to solve this puzzle, you will need to construct a new API in App Connect.  Some hints are below:  

The token needed to execute the manual override the door is located in another Cloudant NoSQL Database called `manualdooroverridecode`.  **Note** there is only one document in this table, so a filter to extract a specific document is not needed.

You will need to construct the token properly in order to open the door.   The token required is a combination of four other tokens present in an array inside of a Cloudant DB object.

Here is a good reference on functions that might be helpful:  http://docs.jsonata.org/string-functions.html

You can find a sample of the JSON output provided by the Cloudant DB Below.  Hint:  There is `JSON Parse` Operation that can be helpful.

```
{
  "keyset": [
    "abcdef",
    "ghijkl",
    "mnopqr",
    "stuvwx"
  ]
}
```