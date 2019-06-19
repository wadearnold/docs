# Overview

A RESTFul service that implements an interface to write files for the [Fedwire Funds Service](https://www.frbservices.org/financial-services/wires/index.html), [a real-time gross settlement funds transfer system operated by the United States Federal Reserve Banks](https://en.wikipedia.org/wiki/Fedwire). These [compatible files](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.445.7645&rep=rep1&type=pdf) include routing instructions that, once received and processed, will debit the funds from the sending bank's reserve account at their Federal Reserve bank and credit the receiving bank's account. Wire transfers sent via Fedwire are completed in the same day, while some are completed instantly.

## FED Intro


```sh
$ curl -s localhost:8086/fed/ach/search?routingNumber=273976369 | jq .
```

```json
    {
    "achParticipants": [
        {
        "routingNumber": "273976369",
        "officeCode": "O",
        "servicingFRBNumber": "071000301",
        "recordTypeCode": "1",
        "revised": "041513",
        "newRoutingNumber": "000000000",
        "customerName": "VERIDIAN CREDIT UNION",
        "achLocation": {
            "address": "1827 ANSBOROUGH",
            "city": "WATERLOO",
            "state": "IA",
            "postalCode": "50702",
            "postalCodeExtension": "0000"
        },
        "phoneNumber": "3192878332",
        "statusCode": "1",
        "viewCode": "1"
        }
    ],
    "wireParticipants": null
    }
```

## What is FED

FED is FedWire and FedACH data from the Federal Reserve Bank Services.  

[source: U.S. DEPARTMENT OF THE TREASURY](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_general.aspx#basic)

The data and formats represent a compilation of the **FedWire** and **FedACH** data from the [Federal Reserve Bank Services site](https://frbservices.org/).

### FedACH Directory

* [FedACH](https://github.com/moov-io/fed/tree/master/docs/FedACHdir.md)

### FedWire Directory

* [FedWire](https://github.com/moov-io/fed/tree/master/docs/fpddir.md)

### Other resources

* [State and Territory Abbreviations](https://github.com/moov-io/fed/docs/Fed_STATE_CODES.md)

### Copyright and Terms of Use

(c) Federal Reserve Banks

By accessing the [data](https://github.com/moov-io/fed/data) in this repository you agree to the [Federal Reserve Banks' Terms of Use](https://frbservices.org/terms/index.html) and the [E-Payments Routing Directory Terms of Use Agreement](https://www.frbservices.org/EPaymentsDirectory/agreement.html).  

## Disclaimer

**THIS REPOSITORY IS NOT AFFILIATED WITH THE FEDERAL RESERVE BANKS AND IS NOT AN OFFICIAL SOURCE FOR THE FEDWIRE AND THE FEDACH DATA.**