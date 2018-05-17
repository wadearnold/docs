## What is ACH
Automated Clearing House (ACH) is an electronic network for financial transactions in the United States. ACH processes large volumes of credit and debit transactions in batches. ACH credit transfers include direct deposit, payroll and vendor payments. ACH direct debit transfers include consumer payments on insurance premiums, mortgage loans, and other kinds of bills. Debit transfers also include new applications such as the point-of-purchase (POP) check conversion pilot program sponsored by the National Automated Clearing House Association (NACHA). Both the government and the commercial sectors use ACH payments. Businesses increasingly use ACH online to have customers pay, rather than via credit or debit cards.

[source: Automated Clearing House](https://en.wikipedia.org/wiki/Automated_Clearing_House)

## How does ACH work? 
NACHA includes Members in the process of establishing Rules for the ACH Network, working collaboratively to create a clear picture of participant roles and responsibilities in the following ACH transaction process.
 

1. An Originator– whether that’s an individual, a corporation or another entity– initiates either a Direct Deposit or Direct Payment transaction using the ACH Network. ACH transactions can be either debit or credit payments and commonly include Direct Deposit of payroll, government and Social Security benefits, mortgage and bill payments, online banking payments, person-to-person (P2P) and business-to-business (B2B) payments, to name a few.
2. Instead of using paper checks, ACH entries are entered and transmitted electronically, making transactions quicker, safer and easier. 
3. The Originating Depository Financial institution (ODFI) enters the ACH entry at the request of the Originator. 
4. The ODFI aggregates payments from customers and transmits them in batches at regular, predetermined intervals to an ACH Operator. 
5. ACH Operators (two central clearing facilities: The Federal Reserve or The Clearing House) receive batches of ACH entries from the ODFI. 
6. The ACH transactions are sorted and made available by the ACH Operator to the Receiving Depository Financial Institution (RDFI). 
7. The Receiver’s account is debited or credited by the RDFI, according to the type of ACH entry. Individuals, businesses and other entities can all be Receivers. 
8. Each ACH credit transaction settles in one to two business days, and each debit transaction settles in just one business day, as per the Rules. 

[source: ACH Network: How it Works](https://www.nacha.org/ach-network)

## Developer Overview

Gusto has provided a great technical overview of how ACH works for developers

- [How ACH works: A developer perspective - Part 1](http://engineering.gusto.com/how-ach-works-a-developer-perspective-part-1/)
- [How ACH works: A developer perspective - Part 2](http://engineering.gusto.com/how-ach-works-a-developer-perspective-part-2/)
- [How ACH works: A developer perspective - Part 3](http://engineering.gusto.com/how-ach-works-a-developer-perspective-part-3/)
- [How ACH works: A developer perspective - Part 4](http://engineering.gusto.com/how-ach-works-a-developer-perspective-part-4/)


## Sequence of records

Overview of Record type file format specification

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
| *10* | 79-79 | 1 | Numeric | Addenda Record Indicator | "0" = no addenda "1" = one addenda included | M |
| *11* | 80-94 | 15 | Numeric | Trace Number | Standard Entry Detail Trace Number | M |