
## What is OFAC

The Office of Foreign Assets Control administers and enforces economic sanctions programs primarily against countries and groups of individuals, such as terrorists and narcotics traffickers. The sanctions can be either comprehensive or selective, using the blocking of assets and trade restrictions to accomplish foreign policy and national security goals. [09-10-02]

[source: U.S. DEPARTMENT OF THE TREASURY](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_general.aspx#basic)

## Running Moov OFAC

You can download a [binary from GitHub](https://github.com/moov-io/ofac/releases) or a [Docker image](https://hub.docker.com/r/moov/ofac) for OFAC. Once downloaded you can start making requests against OFAC. The service will download the latest data on startup.

```
$ docker run -p 8084:8084 -p 9094:9094 -it moov/ofac:v0.5.2
ts=2019-02-26T05:17:06.49074Z caller=main.go:42 startup="Starting ofac server version v0.5.2"
ts=2019-02-26T05:17:06.49086Z caller=main.go:55 main="sqlite version 3.25.2"
ts=2019-02-26T05:17:06.492432Z caller=sqlite.go:73 sqlite="starting database migrations"
ts=2019-02-26T05:17:06.492528Z caller=sqlite.go:83 sqlite="migration #0 [create table if not exists customer_name...] changed 0 rows"
...
ts=2019-02-26T05:17:06.492849Z caller=sqlite.go:87 sqlite="finished migrations"
ts=2019-02-26T05:17:06.493182Z caller=download.go:74 download="Starting refresh of OFAC data"
ts=2019-02-26T05:17:12.058369Z caller=download.go:117 download="Finished refresh of OFAC data"
ts=2019-02-26T05:17:12.061278Z caller=main.go:125 main="OFAC data refreshed - Addresses=11774 AltNames=9748 SDNs=7441"

$ curl -s localhost:8084/search?name=...
{
  "SDNs": [
    {
      "entityID": "...",
      "sdnName": "...",
      "sdnType": "...",
      "program": "...",
      "title": "...",
      "callSign": "...",
      "vesselType": "...",
      "tonnage": "...",
      "grossRegisteredTonnage": "...",
      "vesselFlag": "...",
      "vesselOwner": "...",
      "remarks": "..."
    }
  ],
  "altNames": null,
  "addresses": null
}
```

An SDN (or entity) is an individual, group, or company which has or could do business with United States companies or individuals. US law requires checking OFAC data before transactions.

## Webhooks

OFAC supports registering a callback url (also called [webhook](https://en.wikipedia.org/wiki/Webhook)) for searches or a given entity ID. (API docs: [company](https://api.moov.io/#operation/addCompanyWatch) or [customers](https://api.moov.io/#operation/addCustomerWatch)) This allows services to monitor for changes to the OFAC data. There's an example [app that receives webhooks](https://github.com/moov-io/ofac/blob/master/examples/webhook/webhook.go) written in Go. OFAC sends either a [Company](https://godoc.org/github.com/moov-io/ofac/client#Company) or [Customer](https://godoc.org/github.com/moov-io/ofac/client#Customer) model in JSON to the webhook URL.

Webhook URLs MUST be secure (https://...) and an `Authorization` header is sent with an auth token provided when setting up the webhook. Callers should always verify this auth token matches what was originally provided.

## FAQ

[FAQ](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/ques_index.aspx)

[General Questions](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_general.aspx)

[Sanctions Compliance](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_compliance.aspx)

[Sanction List and Files](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_lists.aspx)

[Iran Sanctions](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_iran.aspx)

[Other Sanction Programs](https://www.treasury.gov/resource-center/faqs/Sanctions/Pages/faq_other.aspx)
