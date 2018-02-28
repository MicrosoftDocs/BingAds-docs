---
title: SetAdExtensionsAssociations Service Operation - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Associates the specified ad extensions with the respective campaigns or ad groups.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
> [!IMPORTANT]
> This Bing Ads API Version 12 preview documentation is subject to change.
# SetAdExtensionsAssociations Service Operation - Campaign Management
Associates the specified ad extensions with the respective campaigns or ad groups.

> [!NOTE]
> Call and Location ad extensions cannot be associated with an ad group. Call ad extensions cannot be associated with an account.

## <a name="request"></a>Request Elements
The *SetAdExtensionsAssociationsRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="accountid"></a>AccountId|The identifier of the account that owns the extensions.|**long**|
|<a name="adextensionidtoentityidassociations"></a>AdExtensionIdToEntityIdAssociations|The list of ad extensions with associated account, campaign, or ad group. You can only associate ad extensions with one type of entity per service call. Specify the entity type with the *AssociationType* element.<br /><br /> Call and Location ad extensions cannot be associated with an ad group. Call ad extensions cannot be associated with an account.<br /><br />You may set a maximum of 100 associations per service call.|[AdExtensionIdToEntityIdAssociation](adextensionidtoentityidassociation.md) array|
|<a name="associationtype"></a>AssociationType|The type of all entities specified in the *AdExtensionIdToEntityIdAssociations* list.|[AssociationType](associationtype.md)|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *SetAdExtensionsAssociationsResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="partialerrors"></a>PartialErrors|An array of [BatchError](../campaign-management-service/batcherror.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](batcherror.md) array|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
The following template shows the order of the [body](#request-body) and [header](#request-header) elements for the SOAP request.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">SetAdExtensionsAssociations</Action>
    <ApplicationToken i:nil="false">ValueHere</ApplicationToken>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <CustomerAccountId i:nil="false">ValueHere</CustomerAccountId>
    <CustomerId i:nil="false">ValueHere</CustomerId>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
    <Password i:nil="false">ValueHere</Password>
    <UserName i:nil="false">ValueHere</UserName>
  </s:Header>
  <s:Body>
    <SetAdExtensionsAssociationsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId>ValueHere</AccountId>
      <AdExtensionIdToEntityIdAssociations i:nil="false">
        <AdExtensionIdToEntityIdAssociation>
          <AdExtensionId>ValueHere</AdExtensionId>
          <EntityId>ValueHere</EntityId>
        </AdExtensionIdToEntityIdAssociation>
      </AdExtensionIdToEntityIdAssociations>
      <AssociationType>ValueHere</AssociationType>
    </SetAdExtensionsAssociationsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
The following template shows the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <SetAdExtensionsAssociationsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError d4p1:type="-- derived type specified here with the appropriate prefix --">
          <Code>ValueHere</Code>
          <Details d4p1:nil="false">ValueHere</Details>
          <ErrorCode d4p1:nil="false">ValueHere</ErrorCode>
          <FieldPath d4p1:nil="false">ValueHere</FieldPath>
          <ForwardCompatibilityMap xmlns:e258="http://schemas.datacontract.org/2004/07/System.Collections.Generic" d4p1:nil="false">
            <e258:KeyValuePairOfstringstring>
              <e258:key d4p1:nil="false">ValueHere</e258:key>
              <e258:value d4p1:nil="false">ValueHere</e258:value>
            </e258:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index>ValueHere</Index>
          <Message d4p1:nil="false">ValueHere</Message>
          <Type d4p1:nil="false">ValueHere</Type>
          <!--These fields are applicable if the derived type attribute is set to EditorialError-->
          <Appealable d4p1:nil="false">ValueHere</Appealable>
          <DisapprovedText d4p1:nil="false">ValueHere</DisapprovedText>
          <Location d4p1:nil="false">ValueHere</Location>
          <PublisherCountry d4p1:nil="false">ValueHere</PublisherCountry>
          <ReasonCode>ValueHere</ReasonCode>
        </BatchError>
      </PartialErrors>
    </SetAdExtensionsAssociationsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<SetAdExtensionsAssociationsResponse> SetAdExtensionsAssociationsAsync(
	long accountId,
	IList<AdExtensionIdToEntityIdAssociation> adExtensionIdToEntityIdAssociations,
	AssociationType associationType)
{
	var request = new SetAdExtensionsAssociationsRequest
	{
		AccountId = accountId,
		AdExtensionIdToEntityIdAssociations = adExtensionIdToEntityIdAssociations,
		AssociationType = associationType
	};

	return (await CampaignManagementService.CallAsync((s, r) => s.SetAdExtensionsAssociationsAsync(r), request));
}
```
```java
static SetAdExtensionsAssociationsResponse setAdExtensionsAssociations(
	java.lang.Long accountId,
	ArrayOfAdExtensionIdToEntityIdAssociation adExtensionIdToEntityIdAssociations,
	AssociationType associationType) throws RemoteException, Exception
{
	SetAdExtensionsAssociationsRequest request = new SetAdExtensionsAssociationsRequest();

	request.setAccountId(accountId);
	request.setAdExtensionIdToEntityIdAssociations(adExtensionIdToEntityIdAssociations);
	request.setAssociationType(associationType);

	return CampaignManagementService.getService().setAdExtensionsAssociations(request);
}
```
```php
static function SetAdExtensionsAssociations(
	$accountId,
	$adExtensionIdToEntityIdAssociations,
	$associationType)
{

	$GLOBALS['Proxy'] = $GLOBALS['CampaignManagementProxy'];

	$request = new SetAdExtensionsAssociationsRequest();

	$request->AccountId = $accountId;
	$request->AdExtensionIdToEntityIdAssociations = $adExtensionIdToEntityIdAssociations;
	$request->AssociationType = $associationType;

	return $GLOBALS['CampaignManagementProxy']->GetService()->SetAdExtensionsAssociations($request);
}
```
```python
response=campaignmanagement_service.SetAdExtensionsAssociations(
	AccountId=AccountId,
	AdExtensionIdToEntityIdAssociations=AdExtensionIdToEntityIdAssociations,
	AssociationType=AssociationType)
```

## Requirements
Service: [CampaignManagementService.svc v11](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v11  
