# AchDictionary

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ACHParticipants** | [**[]AchParticipant**](ACHParticipant.md) |  | [optional] 

# AchParticipant

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**RoutingNumber** | **string** | The institution&#39;s routing number | [optional] 
**OfficeCode** | **string** | Main/Head Office or Branch. O&#x3D;main B&#x3D;branch | [optional] 
**ServicingFRBNumber** | **string** | Servicing Fed&#39;s main office routing number | [optional] 
**RecordTypeCode** | **string** | The code indicating the ABA number to be used to route or send ACH items to the RDFI 0 &#x3D; Institution is a Federal Reserve Bank 1 &#x3D; Send items to customer routing number 2 &#x3D; Send items to customer using new routing number field | [optional] 
**Revised** | **string** | Date of last revision | [optional] 
**NewRoutingNumber** | **string** | Financial Institution&#39;s new routing number resulting from a merger or renumber | [optional] 
**CustomerName** | **string** | Financial Institution Name | [optional] 
**AchLocation** | [**[]AchLocation**](ACHLocation.md) | FEDACH delivery address | [optional] 
**PhoneNumber** | **string** | The Financial Institution&#39;s phone number | [optional] 
**StatusCode** | **string** | Code is based on the customers receiver code 1 &#x3D; Receives Gov/Comm | [optional] 
**ViewCode** | **string** | Code is current view 1 &#x3D; Current view | [optional] 

# AchLocation

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Address** | **string** | Street Address | [optional] 
**City** | **string** | City | [optional] 
**State** | **string** | State | [optional] 
**PostalCode** | **string** | Postal Code | [optional] 
**PostalExtension** | **string** | Postal Code Extension | [optional] 

# WireDictionary

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**WIREParticipants** | [**[]WireParticipant**](WIREParticipant.md) |  | [optional] 

# WireParticipant

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**RoutingNumber** | **string** | The institution&#39;s routing number | [optional] 
**TelegraphicName** | **string** | Short name of financial institution | [optional] 
**CustomerName** | **string** | Financial Institution Name | [optional] 
**WireLocation** | [**[]WireLocation**](WIRELocation.md) | FEDWIRE Delivery Address | [optional] 
**FundsTransferStatus** | **string** | Designates funds transfer status Y &#x3D; Eligible N &#x3D; Ineligible | [optional] 
**FundsSettlementOnlyStatus** | **string** | Designates funds settlement only status S &#x3D; Settlement-Only or blank | [optional] 
**BookEntrySecuritiesTransferStatus** | **string** | Designates book entry securities transfer status Y &#x3D; Eligible N &#x3D; Ineligible | [optional] 
**Date** | **string** | Date of last revision | [optional] 

# WireLocation

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**City** | **string** | City | [optional] 
**State** | **string** | State | [optional] 
