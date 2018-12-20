## Picking which Standard Entry Class Code code to use

The [NACHA Corporate Rules and Guidelines](https://github.com/moov-io/ach/blob/master/documentation/2013-Corporate-Rules-and-Guidelines.pdf) offer a helpful table for choosing the correct Standard Entry Class (SEC) Code to use for a given enrollment and transaction. The table has been copied below:

### Point of Sale Transactiosn

| Physical Enrollment | Internet Enrollment | Telephone Enrollment |
|---|---|---|
| <p>Customer enrolls at a merchant store, a bank branch or in response to a mail solicitation for an ACH-based debit card, and uses the card at a POS terminal.</p><p>Proper SEC Code: **POS**</p> | <p>Customer enrolls at a merchant or bank web site for an ACH-based debit card, and uses the card at a POS terminal.</p><p>Customer enrolls via a mobile device for an ACH-based near-field communication debit service on the device, and uses the mobile device at a POS terminal.</p><p>Proper SEC Code: **POS**</p> | <p>Customer enrolls through a merchant or bank telephone system for an ACH-based debit card, and uses the card at a POS terminal.</p><p>Proper SEC Code: **POS**</p> |

### Internet Transactions

| Physical Enrollment | Internet Enrollment | Telephone Enrollment |
|---|---|---|
| <p>Customer opens account at a bank branch and authorizes debits to transfer funds into the account, and initiates such debits via the bank’s web site.</p><p>Customer enrolls in biller’s or service provider’s bill payment service via mail, and initiates individual bill payments at the biller’s or service provider’s web site.</p><p>Customer enrolls at a merchant store, a bank branch or in response to a mail solicitation for an ACH-based debit card, and uses the card to make a purchase at a web site.</p><p>Proper SEC Code: **PPD**</p> | <p>Customer executes at a bank’s web site an authorization to transfer funds into a savings account, and initiates each transfer via the bank’s web site.</p><p>Customer enrolls at a biller’s or service provider’s web site to pay bills, and initiates individual bill payments at the web site.</p><p>Customer enrolls at a merchant or bank website for an ACH-based debit card, and uses the card to make a purchase at a web site.</p><p>Customer enrolls via a mobile device in his/her biller’s mobile bill presentment and payment service, and initiates individual bill payments via the mobile device.</p><p>Proper SEC Code: **WEB**</p> | <p>Customer enrolls through a biller’s or service provider’s telephone system to pay bills, and initiates individual bill payments at the biller’s or service provider’s web site.</p><p>Customer enrolls through a merchant or bank telephone system for an ACH-based debit card, and uses the card to make a purchase at a web site.</p><p>Proper SEC Code: **PPD**</p> |

## ATM Transactions

| Physical Enrollment | Internet Enrollment | Telephone Enrollment |
|---|---|---|
| <p>Customer enrolls at a merchant store, a bank branch or in response to a mail solicitation for an ACH-based debit card, and uses the card at an ATM to withdraw cash.</p><p>Proper SEC Code: **MTE**</p> | <p>Customer enrolls at a merchant or bank web site for an ACH-based debit card, and uses the card at an ATM to withdraw cash.</p><p>Proper SEC Code: **MTE**</p> | <p>Customer enrolls through a merchant or bank telephone system for an ACH-based debit card, and uses the card at an ATM to withdraw cash.</p><p>Proper SEC Code: **MTE**</p> |
