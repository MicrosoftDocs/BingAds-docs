---
title: "Bing Ads Scripts Builders"
description: "Describes how builders work in Bing Ads Scripts."
author: "brapel"
manager: ehansen

ms.author: "v-brapel"
ms.service: "bingads-scripts"
ms.topic: "article"
---

# What are builders?

[!INCLUDE[preview-note](../includes/preview-note.md)]

To add an entity, you use builders. The following shows the multi-step process for adding an entity. 

1. Get a builder object and use it to specify the entity’s properties. 
2. Call the `build` method to create an operation object. (The builder simply creates the entity’s definition.) 
3. Call any of the operation’s methods to create the entity. Typically, you call the `getResult` method but calling any of the methods creates the entity.

The following example demonstrates how to create a keyword using the builder and operation objects.

```javascript
// Retrieve an ad group.
var adGroup = BingAdsApp.adGroups().get().next();

// Use the 'with' methods to specify the entity's property values.
var keywordBuilder = adGroup.newKeywordBuilder()
    .withCpc(1.2)
    .withText("shirts")
    .withFinalUrl("https://www.contoso.com/shirts");

// Get the operation object that you use to add the entity.
var keywordOperation = keywordBuilder.build();

// The call to isSuccessful() performs the add operation
// and blocks until the operation completes.
if (keywordOperation.isSuccessful()) {
  // Get the result.
  var keyword = keywordOperation.getResult();
} else {
  // Handle the errors.
  var errors = keywordOperation.getErrors();
}
```

## Performance considerations

If you're creating more than one entity, do not execute the operation in the same loop that you use to create the operationa object. Instead, create an array to hold the operations and then iterate through that array to retrieve the results.  

### Poor Performance
``` javascript
for (var i = 0; i < keywords.length; i++)
  var keywordOperation = BingAdsApp.adGroups().get().next()
    .newKeywordBuilder()
    .withText(keywords[i])
    .build();

  // Retrieving the result in the same
  // loop that creates the operation
  // leads to poor performance.
  var newKeyword =
      keywordOperation.getResult();
  newKeyword.applyLabel("New keywords");
}
```

### Good Performance
``` javascript
// Create an array to hold the operations.
var operations = [];

for (var i = 0; i < keywords.length; i++) {
  var keywordOperation = BingAdsApp.adGroups().get().next()
    .newKeywordBuilder()
    .withText(keywords[i])
    .build();
  operations.push(keywordOperation);
}

// Process the operations separately. This allows
// Bing Ads Scripts to group operations into
// batches.
for (var i = 0; i < operations.length; i++) {
  var newKeyword = operations[i].getResult();
  newKeyword.applyLabel("New keywords");
}
```

The following are the possible builders.

- [AdGroupBuilder](../reference/AdGroupBuilder.md)
- [ExpandedTextAdBuilder](../reference/ExpandedTextAdBuilder.md)
- [KeywordBuilder](../reference/KeywordBuilder.md)
- [NegativeKeywordListBuilder](../reference/NegativeKeywordListBuilder.md)

## Next steps

> [!div class="nextstepaction"]
> [Learn about preview mode](../guides/preview-mode.md)