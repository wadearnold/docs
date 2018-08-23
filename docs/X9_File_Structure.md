
### File Structure and Record Types

The following record types are established for Electronic Exchange:

 * 01 File Header Record
 * 10 Cash Letter Header Record
 * 20 Bundle Header Record
 * 25 Check Detail Record
 * 26 Check Detail Addendum A Record
 * 27 Check Detail Addendum B Record
 * 28 Check Detail Addendum C record
 * 31 Return Record
 * 32 Return Addendum A Record
 * 33 Return Addendum B Record
 * 34 Return Addendum C Record
 * 35 Return Addendum D Record
 * 50 Image View Detail Record
 * 52 Image View Data Record
 * 54 Image View Analysis Record
 * 62 Credit Record
 * 68 User Record
 * 70 Bundle Control Record
 * 85 Routing Number Summary Record
 * 90 Cash Letter Control Record
 * 99 File Control Record

## Annotated X9 Record Formats

### 01 File Header Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |
| *2* | 03–04 | 2 | N | Standard Level | M |
| *3* | 05–05 | 1 | A | Test File Indicator | M |
| *4* | 06–14 | 9 | N | Immediate Destination Routing Number | M |
| *5* | 15-23 | 9 | N | Immediate Origin Routing Number | M|
| *6* | 24–31 | 8 | N | File Creation Date | M |
| *7* | 32–35 | 4 | N | File Creation Time | M |
| *8* | 36–36 | 1 | A | Resend Indicator | M |
| *9* | 37–54 | 18 | ANS | Immediate Destination Name |  C |
| *10* | 55–72 | 18 | ANS | Immediate Origin Name | C |
| *11* | 73–73 | 1 | AN | File ID Modifier | C|
| *12* | 74–75 | 2 | A | Country Code | C |
| *13* | 76–79 | 4 | ANS | User Field | C |
| *14* | 80-80 | 1 | AN | Companion Document Indicator | C |

All fields that are conditional and are not used shall be filled with Blanks.

### 10 Cash Letter Header Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |
| *2* | 03–04 | 2 | N | Collection Type Indicator | M |
| *3* | 05–13 | 9 | N | Destination Routing Number | M |
| *4* | 14–22 | 9 | N | ECE Institution Routing Number | M |
| *5* | 23-30 | 8 | N | Cash Letter Business Date | M|
| *6* | 31–38 | 8 | N | Cash Letter Creation Date | M |
| *7* | 39-42 | 4 | N | Cash Letter Creation Time | M |
| *8* | 43-43 | 1 | A | Cash Letter Record Type Indicator | M |
| *9* | 44–44 | 1 | AN | Cash Letter Documentation Type Indicator |  C |
| *10* | 45-52 | 8 | AN | Cash Letter ID | M |
| *11* | 53-66 | 14 | ANS | Originator Contact Name | C|
| *12* | 67-76 | 10 | N | Originator Contact Phone Number | C |
| *13* | 77-77 | 1 | AN | Fed Work Type | C |
| *14* | 78-78 | 1 | A | Returns Indicator | M |
| *15* | 79-79 | 1 | ANS | User Field | C |
| *16* | 80-80 | 1 | B | Reserved | M |

All fields that are conditional and are not used shall be filled with Blanks.

### 20 Bundle Header Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |
| *2* | 03–04 | 2 | 	N | Collection Type Indicator |	M |
| *3* | 05–13 | 9 |	N | Destination Routing Number | M |
| *4* | 14–22 | 9 |	N | ECE Institution Routing Number | M |
| *5* | 23–30 | 8 |	N | Bundle Business Date | M |
| *6* | 31–38 | 8 |	N | Bundle Creation Date | M |
| *7* | 39–48 | 10 | AN	| Bundle ID	 | C |
| *8* | 49–52 | 4 | NB | Bundle Sequence Number | C |
| *9* | 53–54 | 2 |	AN |Cycle Number | C |
| *10* | 55–63 | 9 |	 B | Reserved | M |
| *11* | 64–68 | 5 |	 ANS | User Field | C |
| *12* | 69–80 |	 12 | B | Reserved | M |

All fields that are conditional and are not used shall be filled with Blanks.

### 25 Check Detail Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |	
| *2* |	03–17 | 15 | NBSM | Auxiliary On-Us | C |	
| *3* |	18–18 | 1 | NS | External Processing Code | C |	
| *4* |	19–26 | 8 | N | Payor Bank Routing Number | M |
| *5* |	27–27 | 1 | N | Payor Bank Routing Number Check Digit | M | 
| *6* |	28–47 | 20 | NBSMOS | On-Us | C |  
| *7* |	48–57 | 10 | N | Item Amount	 | M |	 
| *8* |	58–72 | 15 | NB | ECE Institution Item Sequence Number | M |	 
| *9* |	73–73 | 1 | AN | Documentation Type Indicator | C |	 
| *10* | 74–74 | 1 | AN | Return Acceptance Indicator | C |	 
| *11* | 75–75 | 1 | N | MICR Valid Indicator | C |	 
| *12* | 76–76 | 1 | A | BOFD Indicator | M |	 
| *13* | 77–78 | 2 | N | Check Detail Record Addendum Count | M |	 
| *14* | 79–79 | 1 | N | Correction Indicator | C |	 
| *15* | 80-80 | 1 | AN | Archive Type Indicator | C | 

All fields that are conditional and are not used shall be filled with Blanks.

### 26 Check Detail Addendum A Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |
| *2* | 03–03 | 1 | N | Check Detail Addendum A Record Number | M |
| *3* | 04–12 | 9 | N | Return Location Routing Number | M |
| *4* | 13–20 | 8 | N | 	BOFD / Endorsement Date | M |
| *5* | 21–35 | 15 | NB | BOFD Item Sequence Number | C |
| *6* | 36–53 | 18 | ANS | Deposit Account Number at BOFD  | C |
| *7* | 54–58 | 5 | ANS | BOFD Deposit Branch | C |
| *8* | 59–73 | 15 | ANS | Payee Name | C |
| *9* | 74-74 | 1 | A | Truncation Indicator | M |
| *10* | 75-75 | 1 | AN | BOFD Conversion Indicator | C |
| *11* | 76-76 | 1 | N | BOFD Correction Indicator | C |
| *12* | 77-77 | 1 | ANS | User Field | C |
| *13* | 78-80 | 3 | B | Reserved | M |

All fields that are conditional and are not used shall be filled with Blanks.

### 27 Check Detail Addendum B Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01-02 | 2 | N | Record Type | M |
| *2* | 03–03 | 1 | 	N | Image Reference Key Indicator | M |
| *3* | 04–18 | 15 |	 NB | Microfilm Archive Sequence Number| C |
| *4* | 19–22 | 4 |	N | Length of Image Reference Key | M |
| *5* | 23–(22+X) | Variable X | ANS | Image Reference Key, X = value in Length of Image Reference Key| C |
| *6* | (23+X)–(37+X) | 15 | ANS | Description | C |
| *7* | (38+X)–(41+X) | 4 | 	ANS | User Field | C |
| *8* | (42+X)–(46+X) | 5 | B | Reserved | M |

All fields that are conditional and are not used shall be filled with Blanks.

### 28 Check Detail Addendum C Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |
| *2* | 03–04 | 2 | 	N | Check Detail Addendum C Record Number |	M |
| *3* | 05–13 | 8 |	N | Endorsing Bank Routing Number | M |
| *4* | 14–21 | 9 |	N | BOFD / Endorsement Business Date | M |
| *5* | 22–36 | 15 | NB | Endorsing Bank Item Sequence Number | M |
| *6* | 37–37 | 1 | A | Truncation Indicator | C |
| *7* | 38–38 | 1 | AN | Endorsing Bank Conversion Indicator	 | C |
| *8* | 39–39 | 1 | A | Endorsing Bank Correction Indicator | C |
| *9* | 40–40 | 1 | AN | Return Reason | C |
| *10* | 41–59 | 19 | ANS | User Field | C |
| *11* | 60–60 | 1 | AN | Endorsing Bank Identifier | C |
| *12* | 61–80 | 20 | B | Reserved | M |

All fields that are conditional and are not used shall be filled with Blanks.

### 70 Bundle Control Record 

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* | 01–02 | 2 | N | Record Type | M |
| *2* | 03–06 | 4 | 	N | Items Within Bundle Count |	M |
| *3* | 07–18 | 12 |	N | Bundle Total Amount | M |
| *4* | 19–30 | 12 |	N | MICR Valid Total Amount	 | C |
| *5* | 31–35 | 5 |	N | Images within Bundle Count | M |
| *6* | 36–55 | 20 |	ANS | User Field | C |
| *7* | 56–56 | 1 | N	| Bundle ID	 | C |
| *8* | 57–80 | 24 | B | Bundle Sequence Number | M |

All fields that are conditional and are not used shall be filled with Blanks.

### 90 Cash Letter Control Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* |	01–02 | 2 | N | Record Type	| M |
| *2* |	03-08 | 6 | N | Bundle Count | M | 
| *3* | 09-16 | 8 | N | Items Within Cash letter Count | M |
| *4* |	17-30 | 14 | N | Cash Letter Total Amount | M |
| *5* |	31-39 | 9 | N | Images Within Cash Letter Count | M |
| *6* |	40–57 | 18 | ANS | ECE Institution Name | C |
| *7* |	58-65 | 8 | N | Settlement Date | C |
| *8* |	66-66 | 1 | N | Credit Total Indicator | C |
| *9* |	67–80 | 14 | B | Reserved |	M |

All fields that are conditional and are not used shall be filled with Blanks.

### 99 File Control Record

| Field | Position | Size | Type | Field Name | Usage - M, C |
| :---: | :---: | :---: | :---: | :--- | :---: |
| *1* |	01–02 | 2 | N | Record Type	| M |
| *2* |	03-08 | 6 | N | Cash Letter Count | M | 
| *3* | 09-16 | 8 | N | Total Record Count | M |
| *4* | 17-24 | 8 | N | Total Item Count | M |
| *5* | 25-40 | 16 | N | File Total Amount | M |
| *6* | 41-54 | 14 | ANS | Immediate Origin Contact Name | C |
| *7* |	55-64 | 10 | N | Immediate Origin Contact Phone Number | C |
| *8* |	65-65 | 1 | N | Credit Total Indicator | C |
| *9* |	66-80 | 15 | B | Reserved |	M |

All fields that are conditional and are not used shall be filled with Blanks.







