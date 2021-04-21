---
name: Query Rules searchTermContains multiple search terms
keywords: query rules, search terms, several, multiple, more than one, searchTermContains, or, or operator
dateUpdated: 4/21/21
product: Answers
categories: backend, query rules
communityLinks:
imageURL:
---

## Overview

When writing query rules to prescibe search behavior, the searchTermContains criteria can be used to trigger a rule when the query contains defined terms. This will do a token match on the search term. If multiple tokens are included, it will make sure they are all present.

For example, the value: 
```json 
["Heart attack","911"]
```
would trigger the rule in the case the query contains both "Heart attack" and "911".

If, instead, you wanted to make the logic "or" (i.e., trigger the rule when at least 1 of the terms is in the query), you could use searchTermMatchesRegex, using | as an OR operator.

## The Code
For example, putting the criteria below in the JSON of your query rule would trigger the query rule whenever a query contains "Heart attack" OR "911":

```json
"criteria": {
    "searchTermMatchesRegex": [ ".*(heart attack|911).*"]
}
```
Multiple terms, each separated by the | OR operater, can be added.

## The Result

The result of this code is that the query rule would now be triggered on searches containing either "Heart attack" or "911". For example, if the [action](https://hitchhikers.yext.com/modules/ans302-query-rules/03-boost-bury-entities/) associated with this rule was to boost urgent care locations, this action would be triggered for any of the following example searches:
* "symptoms of a heart attack"
* "when to call 911"
*  "should I call 911 if I am having a heart attack"

This can help you avoid having to write multiple query rules that trigger the same action.

## Additional Resources
Additional background on criteria for query rules can be found on [Hitchhikers](https://hitchhikers.yext.com/modules/ans302-query-rules/02-criteria/)

Plus, here are some good resources to learn more about using regex:

* https://regexone.com/ - Walks through exercises of regex examples
* https://regex101.com/ - Allows you to test and validate your regex

