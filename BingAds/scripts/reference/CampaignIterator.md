---
title: "CampaignIterator object"
description: "Contains the methods for iterating through a list of campaigns."
author: "brapel"
manager: ehansen

ms.author: "v-brapel"
ms.service: "bingads-scripts"
ms.topic: "article"
---

# CampaignIterator

Contains the methods for iterating through a list of campaigns. For information about Iterators, see [Iterators](../concepts/iterators.md).

Example usage:
```javascript
var campaignSelector = BingAdsApp.campaigns();
var campaignIterator = campaignSelector.get();
while (campaignIterator.hasNext()) {
  var campaign = campaignIterator.next();
}
```

## Methods
|Method Name|Return Type|Description|
|-|-|-
[hasNext](#hasnext)|Boolean|Returns a Boolean value that indicates whether the iterator has more elements.
[next](#next)|[Campaign](./Campaign)|Advances the iterator and returns the next campaign.
[totalNumEntities](#totalnumentities)|int|Returns the number of campaigns that matched the selector's selection criteria.

## <a name="hasnext"></a>hasNext
Returns a Boolean value that indicates whether the iterator has more elements.

### Returns
|Type|Description|
|-|-
Boolean|Returns **true** if the iterator has more elements; otherwise, **false**.

## <a name="next"></a>next
Advances the iterator and returns the next campaign.

### Returns
|Type|Description|
|-|-
[Campaign](Campaign.md)|The next campaign in the iterator.

## <a name="totalnumentities"></a>totalNumEntities
Returns the number of campaigns that matched the selector's selection criteria. 

[!INCLUDE[reads-limit](../includes/reads-limit.md)]

### Returns:
|Type|Description|
|-|-
int|The number of campaigns that matched the selector's selection criteria.



## See also
- [CampaignSelector.get()](CampaignSelector.md#get)
- [Campaign](Campaign.md)