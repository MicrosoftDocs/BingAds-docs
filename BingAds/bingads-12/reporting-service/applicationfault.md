---
title: ApplicationFault Data Object - Reporting
ms.service: bing-ads-reporting-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Defines the base object from which all fault detail objects derive.
---
> [!IMPORTANT]
> This Bing Ads API Version 12 preview documentation is subject to change.

# ApplicationFault Data Object - Reporting
Defines the base object from which all fault detail objects derive.

## Syntax
```xml
<xs:complexType name="ApplicationFault" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:sequence>
    <xs:element minOccurs="0" name="TrackingId" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="trackingid"></a>TrackingId|The identifier of the log entry that contains the details of the API call.|**string**|

## Requirements
Service: [ReportingService.svc v12](https://reporting.api.bingads.microsoft.com/Api/Advertiser/Reporting/v11/ReportingService.svc)  
Namespace: https\://adapi.microsoft.com  
