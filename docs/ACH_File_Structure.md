#ACH File Structure

## Sequence of Records and Description

Each NACHA formatted file you originate consists of the following records:

* A File Header Record,
* One or more Company/Batch Header Record(s),
* Entry Detail Record(s),
* Addenda Record(s), if allowed and you choose to include them, or if required One or more Company/Batch Control Record(s) and,
* A File Control Record.

Each file begins with a File Header record. Following the File Header Record may be any number of batches. Each batch is identified by a Batch Header Record and contains one or more Entry Detail Records. At the end of each batch is a Batch Control Record. Each file is ended with a File Control Record.
The diagram on the following page illustrates the Sequence of Records for ACH entries. The sequence of records will always be the same, regardless of SEC code. Out-of- sequence records or lack of a mandatory record will cause all or portions of the file to reject. Padding with “9” records at the end of the file is optional.

## Input File Descriptions

### File Header

The File Header Record designates physical file characteristics and identifies the immediate origin of the entries contained within the file or within the transmitted batched data. In addition, this record includes date, time, and file identification fields that can be used to uniquely identify the file.

### Company/Batch Header Record

The Company/Batch Header Record identifies the Originator and briefly describes the purpose of the entries that are contained within the batch. For example, “GAS BILL” or “REG SALARY” indicates the reason for the transaction originated by the Originator. It also indicates the intended effective entry date of all transactions within the batch. The information contained in the Company/Batch Header Record applies uniformly to all subsequent Entry Detail Records in the batch.
If you wish to vary any of this information, you must create a separate batch. For example, if you are making regular payroll payments and bonus payments then you should create one batch described as “REG SALARY” and another as “BONUS.”

### Entry Detail Record

Entry Detail Records contain information that relate the specific entry to the Receiver, such as the Receiving Depository Financial Institution account and routing transit number and the debit or credit amount.
Prenotifications (prenotes) are special zero-dollar entries used to test the validity of the account number and transit routing number provided by the Receiver. Prenotes are identical to the basic Entry Detail format but contain appropriate Transaction Codes and zeroes in the amount field. Prenotes can be batched with other dollar entries or batched separately.
Zero-dollar entries used in corporate trade payments to deliver remittance information contain appropriate Transaction Codes and zeros in the Amount field but otherwise are formatted the same as other entries. Zero-dollar entries can be batched with other CCD dollar entries or batched separately. One Addenda Record must accompany a CCD zero- dollar entry.

### Addenda Records

For non-IAT entries, Addenda Records are used by the Originator to supply additional information about Entry Detail Records to the Receiver. For many types of entries, such as payroll, addenda records are optional. Addenda Records are usually required for tax payments.

### Company/Batch Control Record

The Company/Batch Control Record contains the counts, hash totals, and total dollar controls for the preceding detail entries within the indicated batch.
All Entry Detail Records are hashed. (The method for calculating hash totals is provided in the Entry Information column in the Record Layouts.) Both Entry Detail Records and Addenda Records are included in the entry/addenda counts; Batch Header and Batch Control Records are not included.

### File Control Record

The File Control Record contains dollar, entry, and hash total accumulations from the Company/Batch Control Records in the file. This record also contains counts of the number of blocks and the number of batches within the file (or batched data transmitted to a single destination).

## NACHA Data Entry Specifications

All alphanumeric and alphabetic fields must be left justified and space filled. All numeric fields must be right justified, unsigned, and zero filled. Characters used in ACH records are restricted to 0-9, A-Z, space, and those special characters which have an EBCDIC value greater than hexadecimal "3F" or an ASCII value greater than hexadecimal "1F.” Occurrences of values EBCDIC "00" - "3F" and ASCII "00" - "1F" are not valid.
Do not use characters that do not meet these requirements.

### Field Inclusion Requirements

The following information defines the requirement for inclusion of certain data fields in ACH entries. These designations are: Mandatory (M), Required (R), and Optional (O).

* **Mandatory.** A “Mandatory” field contains information necessary to ensure the proper routing and/or posting of an ACH entry. The ACH Operator will reject any entry or batch, which does not have appropriate values in a Mandatory field. Bank of America will edit for these same values so that your entries will not reject further down in the processing stream.
* **Required.** The omission of a “Required” field will not cause an entry reject at the ACH Operator, but may cause a reject at the RDFI. For example, if the DFI Account Number field in the Entry Detail Record is omitted, the RDFI may return the entry because it cannot be posted. You should include appropriate values in “Required” fields to avoid processing and control problems at the RDFI.
* **Optional.** The inclusion or omission of an “Optional” data field is at the discretion of the Originator. If you do include optional fields, the RDFI must include them in any return.

## Annotated NACHA Record Formats

### File Header Record - All Formats

The File Header Record designates physical file characteristics. It also identifies the Bank as the immediate destination and your company as the immediate origin of the file.

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '1' | Record Type Code | Code Identifying the File Header Record is '1' | M |
| *2* | 02-03 | 2 | '01' | Priority Code | Currently, only "01" is used | R |
| *3* | 04-13 | 10 | bNNNNNNNNN | Immediate Destination | The Immediate Destination Field identifies the party to which the file is being delivered. Usually the Routing Number of the ACH operator  | M |
| *4* | 14-23 | 10 | NNNNNNNNNN | Immediate Origin | The Immediate Origin Field identifies the sender of the file. | M |
| *5* | 24-29 | 6 | YYMMDD | File Creation Date | The date you create or transmit the input file: <br> “YY” = Last two digits of the Year <br> “MM” = Month in two digits <br> “DD” = Day in two digits | M |
| *6* | 30-33 | 4 | HHMM | File Creation Time | Time of day you create or transmit the input file. This field is used to distinguish among input files if you submit more than one per day: <br>  “HH = Hour based on a 24 hr clock <br >“MM” = Minutes in two digits | O |
| *7* | 34-34 | 1 |  UPPER CASE A-Z (or 0-9) | File ID Modifier | Code to distinguish among multiple input files sent per day. Label the first (or only) file “A” (or “0”) and continue in sequence. | M |
| *8* | 35-37 | 3 | "094" | Record Size | Number of bytes per record-always 94. | M |
| *9* | 38-39 | 2 | "10" | Blocking Factor | Number of records per block | M |
| *10* | 40-40 | 1 | "1" | Format Code | Currently only “1” is used | M |
| *11* | 41-63 | 23 | Alphanumeric | Immediate Destination Name | This field contains the name of the ACH Operator or Receiving Point for which that File is destined | M |
| *12* | 64-86 | 23 | Alphanumeric | Immediate Origin or Company Name | This field contains the name of the ACH Operator or Sending Point that is Transmitting the File | M |
| *13* | 87-94 | 8 | Alphanumeric | Reference Code | You may use this field to describe the input file for internal accounting purposes or fill with spaces. | O |


### RCK (Represented Check Entries)

RCK Entry Detail Record is a physical check that was presented but returned because of insufficient funds may be represented as an ACH entry.

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '6' | Record Type Code | Code Identifying the Entry Detail Record is '6' | M |
| *2* | 02-03 | 2 | Numeric | Transaction Code | Two-digit code that identifies checking account credits/debits | M |
| *3* | 04-11 | 8 | TTTTAAAA | Receiving DFI Identification | Routing Transit number of the receivers financial institution | M |
| *4* | 12-12 | 1 | Numeric | Check Digit | The ninth character of the RDFI Routing Transit Number. Used to check for transpositions. | M |
| *5* | 13-29 | 17 | Alphameric | DFI Account Number | Receiver's account number at the RDFI, a value found on the MICR line of a check| R |
| *6* | 30-39 | 10 | $$$$$$$$¢¢ | Amount | Entry amount in dollars with two decimal places. | M |
| *7* | 40-54 | 15 | Alphameric | Check Serial Number |The serial number of the check being represented | M |
| *8* | 55-76 | 22 | Alphameric | Individual Name | Receiver's Name | M |
| *9* | 77-78 | 2 | Alphameric | Discretionary Data | The use of this field is defined byu the ODFI | O |
| *10* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda <br>"1" = one addenda included | M |
| *11* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

## POP (Point-of-Purchase)

**Point-of-Purchase Entry.** A check presented in-person to a merchant for purchase is presented as an ACH entry instead of a physical check.

This ACH debit application is used by originators as a method of payment for the in-person purchase of goods or services by consumers. These Single Entry debit entries are initiated by the originator based on a written authorization and account information drawn from the source document (a check) obtained from the consumer at the point-of-purchase. The source document, which is voided by the merchant and returned to the consumer at the point-of-purchase, is used to collect the consumer’s routing number, account number and check serial number that will be used to generate the debit entry to the consumer’s account.

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '6' | Record Type Code | Code Identifying the Entry Detail Record is '6' | M |
| *2* | 02-03 | 2 | Numeric | Transaction Code | Two-digit code that identifies checking account credits/debits | M |
| *3* | 04-11 | 8 | TTTTAAAA | Receiving DFI Identification | Routing Transit number of the receivers financial institution | M |
| *4* | 12-12 | 1 | Numeric | Check Digit | The ninth character of the RDFI Routing Transit Number. Used to check for transpositions. | M |
| *5* | 13-29 | 17 | Alphameric | DFI Account Number | Receiver's account number at the RDFI, a value found on the MICR line of a check| R |
| *6* | 30-39 | 10 | $$$$$$$$¢¢ | Amount | Entry amount in dollars with two decimal places. | M |
| *7* | 40-48 | 9 | Alphameric | Check Serial Number |The serial number of the check being represented | M |
| *8* | 49-52 | 22 | Alphameric | Terminal City | Identifies the city in which the electronic terminal is located | M |
| *9* | 53-54 | 2 | Alphameric | Terminal State | Identifies the state in which the electronic terminal is located | M |
| *10* | 55-76 | 22 | Alphameric | Individual Name | Receiver's Name | O |
| *11* | 77-78 | 2 | Blank | Discretionary Data | The use of this field is defined byu the ODFI | O |
| *12* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda <br>"1" = one addenda included | M |
| *13* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

## BOC (Back Office Conversation)

**Back Office Conversion Entry.** A single entry debit initiated at the point of purchase or at a manned bill payment location to transfer funds through conversion to an ACH debit entry during back office processing. Unlike ARC entries, BOC conversions require the customer to be present and a notice that checks may be converted to BOC ACH entries be posted.

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '6' | Record Type Code | Code Identifying the Entry Detail Record is '6' | M |
| *2* | 02-03 | 2 | Numeric | Transaction Code | Two-digit code that identifies checking account credits/debits | M |
| *3* | 04-11 | 8 | TTTTAAAA | Receiving DFI Identification | Routing Transit number of the receivers financial institution | M |
| *4* | 12-12 | 1 | Numeric | Check Digit | The ninth character of the RDFI Routing Transit Number. Used to check for transpositions. | M |
| *5* | 13-29 | 17 | Alphameric | DFI Account Number | Receiver's account number at the RDFI, a value found on the MICR line of a check| R |
| *6* | 30-39 | 10 | $$$$$$$$¢¢ | Amount | Entry amount in dollars with two decimal places. | M |
| *7* | 40-54 | 9 | Alphameric | Check Serial Number |The serial number of the check being represented | M |
| *8* | 55-76 | 22 | Alphameric | Individual Name | Receiver's Name | O |
| *9* | 77-78 | 2 | Blank | Discretionary Data | The use of this field is defined byu the ODFI | O |
| *10* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda <br>"1" = one addenda included | O |
| *11* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

## ARC (Accounts Receivable Entry)

**Accounts Receivable Entry.** A consumer check converted to a one-time ACH debit. The difference between ARC and POP is that ARC can result from a check mailed in where as POP is in-person.

The Accounts Receivable (ARC) Entry provides billers the opportunity to initiate single-entry ACH
debits to customer accounts by converting checks at the point of receipt through the U.S. mail, at
a drop box location or in-person for payment of a bill at a manned location. The biller is required
to provide the customer with notice prior to the acceptance of the check that states the receipt of
the customer’s check will be deemed as the authorization for an ARC debit entry to the customer’s
account. The provision of the notice and the receipt of the check together constitute authorization
for the ARC entry. The customer’s check is solely be used as a source document to obtain the routing
number, account number and check serial number. 


| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '6' | Record Type Code | Code Identifying the Entry Detail Record is '6' | M |
| *2* | 02-03 | 2 | Numeric | Transaction Code | Two-digit code that identifies checking account credits/debits | M |
| *3* | 04-11 | 8 | TTTTAAAA | Receiving DFI Identification | Routing Transit number of the receivers financial institution | M |
| *4* | 12-12 | 1 | Numeric | Check Digit | The ninth character of the RDFI Routing Transit Number. Used to check for transpositions. | M |
| *5* | 13-29 | 17 | Alphameric | DFI Account Number | Receiver's account number at the RDFI, a value found on the MICR line of a check| R |
| *6* | 30-39 | 10 | $$$$$$$$¢¢ | Amount | Entry amount in dollars with two decimal places. | M |
| *7* | 40-54 | 9 | Alphameric | Check Serial Number |The serial number of the check being represented | M |
| *8* | 55-76 | 22 | Alphameric | Individual Name | Receiver's Name | O |
| *9* | 77-78 | 2 | Blank | Discretionary Data | The use of this field is defined byu the ODFI | O |
| *10* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda <br>"1" = one addenda included | O |
| *11* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

## POS (Point-of-Sale)

**Point of Sale Entry.** A POS Entry is a debit Entry initiated at an “electronic terminal” to a Consumer Account of the Receiver to pay an obligation incurred in a point- of-sale transaction, or to effect a point-of-sale terminal cash withdrawal.

Point-of-Sale Entries (POS) are ACH debit entries typically initiated by the use of a merchant-issued plastic card to pay an obligation at the point-of-sale. Much like a financial institution issued debit card, the merchant- issued debit card is swiped at the point-of-sale and approved for use; however, the authorization only verifies the card is open, active and within the card’s limits—it does not verify the Receiver’s account balance or debit the account at the time of the purchase. Settlement of the transaction moves from the card network to the ACH Network through the creation of a POS entry by the card issuer to debit the Receiver’s account.

#### POS Entry Detail Record

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '6' | Record Type Code | Code Identifying the Entry Detail Record is '6' | M |
| *2* | 02-03 | 2 | Numeric | Transaction Code | Two-digit code that identifies checking account credits/debits | M |
| *3* | 04-11 | 8 | TTTTAAAA | Receiving DFI Identification | Routing Transit number of the receivers financial institution | M |
| *4* | 12-12 | 1 | Numeric | Check Digit | The ninth character of the RDFI Routing Transit Number. Used to check for transpositions. | M |
| *5* | 13-29 | 17 | Alphameric | DFI Account Number | Receiver's account number at the RDFI, a value found on the MICR line of a check| R |
| *6* | 30-39 | 10 | $$$$$$$$¢¢ | Amount | Entry amount in dollars with two decimal places. | M |
| *7* | 40-54 | 9 | Alphameric | Individual Identification Number |The serial number of the check being represented | O |
| *8* | 55-76 | 22 | Alphameric | Individual Name | Receiver's Name | R |
| *9* | 77-78 | 2 | Alphameric | Card Transaction Type | This code is used by card processors to identify the type of transaction, such as a purchase, cash advance, or reversal. Values for this field are assigned by the major card Organizations. Code Values: <br>01	Purchase of goods or services <br>02	Cash <br>03	Return Reversal <br>11	Purchase Reversal <br>12	Cash Reversal <br>13	Return <br>21	Adjustment <br>99	Miscellaneous Transaction | M |
| *10* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda <br>"1" = one addenda included | M |
| *11* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

#### POS Addenda Record

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '7' | Record Type Code | Code Identifying the Entry Detail Record is '7' | M |
| *2* | 02-03 | 2 | '02' | Addenda Type Code | The Addenda Type Code defines the specific interpretation and format for the addenda information contained in the Entry. | M |
| *3* | 04-10 | 7 | Alphameric | Reference Information #1 | This field may be used for additional reference numbers, identification numbers, or codes that the merchant needs to identify the particular transaction or customer. | O |
| *4* | 11-13 | 3 | Alphameric | Reference Information #2 | This field may be used for additional reference numbers, identification numbers, or codes that the merchant needs to identify the particular transaction or customer. | O |
| *5* | 14-19 | 6 | Alphameric | Terminal Identification Code | This field identifies an Electronic terminal with a unique code that allows a terminal owner and/or switching network to identify the terminal at which an Entry originated. | R |
| *6* | 20-25 | 6 | Alphameric | Transaction Serial Number | Entry amount in dollars with two decimal places. | R |
| *7* | 26-29 | 4 | MMDD | Transaction Date | This date, expressed MMDD, identifies the date on which the transaction occurred. | R |
| *8* | 30-35 | 6 | Alphameric | Authorization Code or Card Expiration Date | This field indicates the code that a card authorization center has furnished to the merchant. | O |
| *9* | 36-62 | 27 | Alphameric | Terminal Location | This field identifies the specific location of a terminal (i.e., street names of an intersection, address, etc.) in accordance with the requirements of Regulation E. | R |
| *10* | 63-77 | 2 | Alphameric | Terminal City | Identifies the city in which the electronic terminal is located | R |
| *11* | 78-79 | 2 | Alphameric | Terminal State | Identifies the state in which the electronic terminal is located | R |
| *12* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

## SHR Shared Network Entry

**Shared Network Entry.** A SHR entry a debit Entry initiated at an “electronic terminal,” as that term is defined in Regulation E, to a Consumer Account of the Receiver to pay an obligation incurred in a point-of-sale transaction, or to effect a point-of-sale terminal cash withdrawal. Also an adjusting or other credit Entry related to such debit Entry, transfer of funds, or obligation. SHR Entries are initiated in a shared network where the ODFI and RDFI have an agreement in addition to these Rules to process such Entries.

#### SHR Entry Detail Record

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '6' | Record Type Code | Code Identifying the Entry Detail Record is '6' | M |
| *2* | 02-03 | 2 | Numeric | Transaction Code | Two-digit code that identifies checking account credits/debits | M |
| *3* | 04-11 | 8 | TTTTAAAA | Receiving DFI Identification | Routing Transit number of the receivers financial institution | M |
| *4* | 12-12 | 1 | Numeric | Check Digit | The ninth character of the RDFI Routing Transit Number. Used to check for transpositions. | M |
| *5* | 13-29 | 17 | Alphameric | DFI Account Number | Receiver's account number at the RDFI, a value found on the MICR line of a check| R |
| *6* | 30-39 | 10 | $$$$$$$$¢¢ | Amount | Entry amount in dollars with two decimal places. | M |
| *7* | 40-43 | 4 | MMDD | Card Expiration Date | This code is used by cardholder processors and cardholder Financial Institutions to verify that the card remains valid and that certain security procedures required by various card authorization systems have been met. | R |
| *8* | 44-54 | 11 | Numeric | Document Reference Number | This field further defines the transaction in the event of a Receiver’s inquiry. An example is an Electronic sequence number | R |
| *9* | 55-76 | 22 | Numeric | Individual Card Account Number | The Individual Card Account Number is the number assigned by the card issuer and is obtained from the card itself. | R |
| *10* | 77-78 | 2 | Alphameric | Card Transaction Type | This code is used by card processors to identify the type of transaction, such as a purchase, cash advance, or reversal. Values for this field are assigned by the major card Organizations. Code Values: <br>01	Purchase of goods or services <br>02	Cash <br>03	Return Reversal <br>11	Purchase Reversal <br>12	Cash Reversal <br>13	Return <br>21	Adjustment <br>99	Miscellaneous Transaction | M |
| *11* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda <br>"1" = one addenda included | M |
| *12* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |

#### SHR Addenda Record

| Field | Position | Size | Contents | Field Name | Entry Information | M,R,O |
| :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| *1* | 01-01 | 1 | '7' | Record Type Code | Code Identifying the Entry Detail Record is '7' | M |
| *2* | 02-03 | 2 | '02' | Addenda Type Code | The Addenda Type Code defines the specific interpretation and format for the addenda information contained in the Entry. | M |
| *3* | 04-10 | 7 | Alphameric | Reference Information #1 | This field may be used for additional reference numbers, identification numbers, or codes that the merchant needs to identify the particular transaction or customer. | O |
| *4* | 11-13 | 3 | Alphameric | Reference Information #2 | This field may be used for additional reference numbers, identification numbers, or codes that the merchant needs to identify the particular transaction or customer. | O |
| *5* | 14-19 | 6 | Alphameric | Terminal Identification Code | This field identifies an Electronic terminal with a unique code that allows a terminal owner and/or switching network to identify the terminal at which an Entry originated. | R |
| *6* | 20-25 | 6 | Alphameric | Transaction Serial Number | Entry amount in dollars with two decimal places. | R |
| *7* | 26-29 | 4 | MMDD | Transaction Date | This date, expressed MMDD, identifies the date on which the transaction occurred. | R |
| *8* | 30-35 | 6 | MMDD | Authorization Code or Card Expiration Date | This field indicates the code that a card authorization center has furnished to the merchant. | O |
| *9* | 36-62 | 27 | Alphameric | Terminal Location | This field identifies the specific location of a terminal (i.e., street names of an intersection, address, etc.) in accordance with the requirements of Regulation E. | R |
| *10* | 63-77 | 2 | Alphameric | Terminal City | Identifies the city in which the electronic terminal is located | R |
| *11* | 78-79 | 2 | Alphameric | Terminal State | Identifies the state in which the electronic terminal is located | R |
| *12* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |