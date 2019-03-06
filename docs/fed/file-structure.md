## AchParticipant

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**RoutingNumber** | **string** | The institution&#39;s routing number |
**OfficeCode** | **string** | Main/Head Office or Branch. O&#x3D;main B&#x3D;branch |
**ServicingFRBNumber** | **string** | Servicing Fed&#39;s main office routing number |
**RecordTypeCode** | **string** | The code indicating the ABA number to be used to route or send ACH items to the RDFI 0 &#x3D; Institution is a Federal Reserve Bank 1 &#x3D; Send items to customer routing number 2 &#x3D; Send items to customer using new routing number field | 
**Revised** | **string** | Date of last revision |
**NewRoutingNumber** | **string** | Financial Institution&#39;s new routing number resulting from a merger or renumber |
**CustomerName** | **string** | Financial Institution Name |
**Address** | **string** | Street Address |
**City** | **string** | City | 
**State** | **string** | State |
**PostalCode** | **string** | Postal Code |
**PostalExtension** | **string** | Postal Code Extension |
**PhoneNumber** | **string** | The Financial Institution&#39;s phone number |
**StatusCode** | **string** | Code is based on the customers receiver code 1 &#x3D; Receives Gov/Comm |
**ViewCode** | **string** | Code is current view 1 &#x3D; Current view |

# WireParticipant

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**RoutingNumber** | **string** | The institution&#39;s routing number |
**TelegraphicName** | **string** | Short name of financial institution |
**CustomerName** | **string** | Financial Institution Name |
**City** | **string** | City | [optional] 
**State** | **string** | State | [optional]  
**FundsTransferStatus** | **string** | Designates funds transfer status Y &#x3D; Eligible N &#x3D; Ineligible |
**FundsSettlementOnlyStatus** | **string** | Designates funds settlement only status S &#x3D; Settlement-Only or blank |
**BookEntrySecuritiesTransferStatus** | **string** | Designates book entry securities transfer status Y &#x3D; Eligible N &#x3D; Ineligible |
**Date** | **string** | Date of last revision |

