## The following Tags are mandatory for all transfers

# SenderSupplied, TypeSubType, InputMessageAccountabilityData, Amount, SenderDepositoryInstitution, ReceiverDepositoryInstitution

# SenderSupplied

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**FormatVersion** | **string** | FormatVersion 30  | 
**UserRequestCorrelation** | **string** | UserRequestCorrelation | 
**TestProductionCode** | [**TestProductionCodeEnum**](TestProductionCodeEnum.md) |  | 
**MessageDuplicationCode** | **string** | MessageDuplicationCode  * &#x60; &#x60; - Original Message * &#x60;R&#x60; - Retrieval of an original message * &#x60;P&#x60; - Resend  | 

# TypeSubType

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**TypeCode** | [**TypeCodeEnum**](TypeCodeEnum.md) |  | 
**SubTypeCode** | [**SubTypeCodeEnum**](SubTypeCodeEnum.md) |  | 

# InputMessageAccountabilityData

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**InputCycleDate** | **string** | InputCycleDate CCYYMMDD  | 
**InputSource** | **string** | InputSource | 
**InputSequenceNumber** | **string** | InputSequenceNumber | 

# Amount

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Amount** | **string** | Amount 12 numeric, right-justified with leading zeros, an implied decimal point and no commas; e.g., $12,345.67 becomes 000001234567 Can be all zeros for subtype 90  | 

# SenderDepositoryInstitution

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**SenderABANumber** | **string** | SenderABANumber | 
**SenderShortName** | **string** | SenderShortName | 

# ReceiverDepositoryInstitution

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ReceiverABANumber** | **string** | ReceiverABANumber | 
**ReceiverShortName** | **string** | ReceiverShortName | 

# BusinessFunctionCode

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**BusinessFunctionCode** | [**BusinessFunctionCodeEnum**](BusinessFunctionCodeEnum.md) |  | 
**TransactionTypeCode** | **string** | TransactionTypeCode If {3600} is CTR, an optional Transaction Type Code element is permitted; however, the Transaction Type Code &#39;COV&#39; is not permitted. | [optional] 


## Other Transfer Information

# SenderReference

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**SenderReference** | **string** | SenderReference | [optional] 

# LocalInstrument

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**LocalInstrumentCode** | [**LocalInstrumentEnum**](LocalInstrumentEnum.md) |  | [optional] 
**ProprietaryCode** | **string** | ProprietaryCode | [optional]

# PaymentNotification

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**PaymentNotificationIndicator** | **string** | PaymentNotificationIndicator  * &#x60;0 - 6&#x60; - Reserved for market practice conventions. * &#x60;7 - 9&#x60; - Reserved for bilateral agreements between Fedwire senders and receivers.  | [optional] 
**ContactNotificationElectronicAddress** | **string** | ContactNotificationElectronicAddress | [optional] 
**ContactName** | **string** | ContactName | [optional] 
**ContactPhoneNumber** | **string** | ContactPhoneNumber | [optional] 
**ContactMobileNumber** | **string** | ContactMobileNumber | [optional] 
**FaxNumber** | **string** | FaxNumber | [optional] 
**EndToEndIdentification** | **string** | EndToEndIdentification | [optional] 

# Charges

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ChargeDetails** | **string** | ChargeDetails * &#x60;B&#x60; - Beneficiary * &#x60;S&#x60; - Shared  | [optional] 
**SendersChargesOne** | **string** | SendersChargesOne  The first three characters must contain an alpha currency code (e.g., USD).  The remaining characters for the amount must begin with at least one numeric character (0-9) and only one decimal comma marker.  $1,234.56 should be entered as USD1234,56 and $0.99 should be entered as USD0,99.  | [optional] 
**SendersChargesTwo** | **string** | SendersChargesTwo  The first three characters must contain an alpha currency code (e.g., USD).  The remaining characters for the amount must begin with at least one numeric character (0-9) and only one decimal comma marker.  $1,234.56 should be entered as USD1234,56 and $0.99 should be entered as USD0,99.  | [optional] 
**SendersChargesThree** | **string** | SendersChargesThree  The first three characters must contain an alpha currency code (e.g., USD).  The remaining characters for the amount must begin with at least one numeric character (0-9) and only one decimal comma marker.  $1,234.56 should be entered as USD1234,56 and $0.99 should be entered as USD0,99.  | [optional] 
**SendersChargesFour** | **string** | SendersChargesFour  The first three characters must contain an alpha currency code (e.g., USD).  The remaining characters for the amount must begin with at least one numeric character (0-9) and only one decimal comma marker.  $1,234.56 should be entered as USD1234,56 and $0.99 should be entered as USD0,99.  | [optional] 

# InstructedAmount

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**CurrencyCode** | **string** | CurrencyCode | [optional] 
**Amount** | **string** | Amount  Must begin with at least one numeric character (0-9) and contain only one decimal comma marker (e.g., $1,234.56 should be entered as 1234,56 and $0.99 should be entered as  | [optional] 

# ExchangeRate

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ExchangeRate** | **string** | ExchangeRate is the exchange rate  Must contain at least one numeric character and only one decimal comma marker (e.g., an exchange rate of 1.2345 should be entered as 1,2345).  | [optional] 

## Beneficiary Information

# Intermediary FI

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IdentificationCode** | **string** | IdentificationCode:  * &#x60;B&#x60; - SWIFT Bank Identifier Code (BIC) * &#x60;C&#x60; - CHIPS Participant * &#x60;D&#x60; - Demand Deposit Account (DDA) Number * &#x60;F&#x60; - Fed Routing Number * &#x60;T&#x60; - SWIFT BIC or Bank Entity Identifier (BEI) and Account Number * &#x60;U&#x60; - CHIPS Identifier  | 
**Identifier** | **string** | Identifier | 
**Name** | **string** | Name | 
**Address** | [**Address**](address.md) |  | 

# Beneficiary FI

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IdentificationCode** | **string** | IdentificationCode:  * &#x60;B&#x60; - SWIFT Bank Identifier Code (BIC) * &#x60;C&#x60; - CHIPS Participant * &#x60;D&#x60; - Demand Deposit Account (DDA) Number * &#x60;F&#x60; - Fed Routing Number * &#x60;T&#x60; - SWIFT BIC or Bank Entity Identifier (BEI) and Account Number * &#x60;U&#x60; - CHIPS Identifier  | 
**Identifier** | **string** | Identifier | 
**Name** | **string** | Name | 
**Address** | [**Address**](address.md) |  | 

# Beneficiary

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IdentificationCode** | **string** | IdentificationCode:  * &#x60;1&#x60; - Passport Number * &#x60;2&#x60; - Tax Identification Number * &#x60;3&#x60; - Driver’s License Number * &#x60;4&#x60; - Alien Registration Number * &#x60;5&#x60; - Corporate Identification * &#x60;9&#x60; - Other Identification  | 
**Identifier** | **string** | Identifier | 
**Name** | **string** | Name | 
**Address** | [**Address**](address.md) |  | 

# BeneficiaryReference

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**BeneficiaryReference** | **string** | BeneficiaryReference | [optional]

# AccountDebitedDrawdown

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IdentificationCode** | **string** | Identification Code * &#x60;D&#x60; - Debit  | 
**Identifier** | **string** | Identifier | 
**Name** | **string** | Name | 
**Address** | [**Address**](address.md) |  | [optional]

## Originator Information

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**IdentificationCode** | **string** | IdentificationCode:  * &#x60;1&#x60; - Passport Number * &#x60;2&#x60; - Tax Identification Number * &#x60;3&#x60; - Driver’s License Number * &#x60;4&#x60; - Alien Registration Number * &#x60;5&#x60; - Corporate Identification * &#x60;9&#x60; - Other Identification  | 
**Identifier** | **string** | Identifier | 
**Name** | **string** | Name | 
**Address** | [**Address**](address.md) |  | 

# OriginatorOptionF

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**PartyIdentifier** | **string** | PartyIdentifier  Must be one of the following two formats: 1. /Account Number (slash followed by at least one valid non-space character:  e.g., /123456)  2. Unique Identifier/ (4 character code followed by a slash and at least one valid non-space character:    e.g., SOSE/123-456-789) ARNU: Alien Registration Number CCPT: Passport Number CUST: Customer Identification Number  DRLC/    Driver’s License Number  EMPL/    Employer Number NIDN: National Identify Number  SOSE/    Social Security Number TXID: Tax Identification Number  | [optional] 
**Name** | **string** | Name  Format:  Must begin with Line Code 1 followed by a slash and at least one valid non-space character: e.g., 1/SMITH JOHN.  | [optional] 
**LineOne** | **string** | LineOne  Format: Must begin with one of the following Line Codes followed by a slash and at least one valid non-space character. 1 Name 2 Address 3 Country and Town 4 Date of Birth 5 Place of Birth 6 Customer Identification Number 7 National Identity Number 8 Additional Information  For example: 2/123 MAIN STREET 3/US/NEW YORK, NY 10000 7/111-22-3456  | [optional] 
**LineTwo** | **string** | LineTwo  Format: Must begin with one of the following Line Codes followed by a slash and at least one valid non-space character. 1 Name 2 Address 3 Country and Town 4 Date of Birth 5 Place of Birth 6 Customer Identification Number 7 National Identity Number 8 Additional Information  For example: 2/123 MAIN STREET 3/US/NEW YORK, NY 10000 7/111-22-3456  | [optional] 
**LineThree** | **string** | LineThree  Format: Must begin with one of the following Line Codes followed by a slash and at least one valid non-space character. 1 Name 2 Address 3 Country and Town 4 Date of Birth 5 Place of Birth 6 Customer Identification Number 7 National Identity Number 8 Additional Information  For example: 2/123 MAIN STREET 3/US/NEW YORK, NY 10000 7/111-22-3456  | [optional] 
 
# Originator FI
 
 Name | Type | Description | Notes
 ------------ | ------------- | ------------- | -------------
 **IdentificationCode** | **string** | IdentificationCode:  * &#x60;B&#x60; - SWIFT Bank Identifier Code (BIC) * &#x60;C&#x60; - CHIPS Participant * &#x60;D&#x60; - Demand Deposit Account (DDA) Number * &#x60;F&#x60; - Fed Routing Number * &#x60;T&#x60; - SWIFT BIC or Bank Entity Identifier (BEI) and Account Number * &#x60;U&#x60; - CHIPS Identifier  | 
 **Identifier** | **string** | Identifier | 
 **Name** | **string** | Name | 
 **Address** | [**Address**](address.md) |  
 
# Instructing FI
  
 Name | Type | Description | Notes
 ------------ | ------------- | ------------- | -------------
 **IdentificationCode** | **string** | IdentificationCode:  * &#x60;B&#x60; - SWIFT Bank Identifier Code (BIC) * &#x60;C&#x60; - CHIPS Participant * &#x60;D&#x60; - Demand Deposit Account (DDA) Number * &#x60;F&#x60; - Fed Routing Number * &#x60;T&#x60; - SWIFT BIC or Bank Entity Identifier (BEI) and Account Number * &#x60;U&#x60; - CHIPS Identifier  | 
 **Identifier** | **string** | Identifier | 
 **Name** | **string** | Name | 
 **Address** | [**Address**](address.md) |
 
# AccountCreditedDrawdown
 
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**DrawdownCreditAccountNumber** | **string** | DrawdownCreditAccountNumber  9 character ABA  | [optional]

# OriginatorToBeneficiary

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**LineOne** | **string** | LineOne | [optional] 
**LineTwo** | **string** | LineTwo | [optional] 
**LineThree** | **string** | LineThree | [optional] 
**LineFour** | **string** | LineFour | [optional]     