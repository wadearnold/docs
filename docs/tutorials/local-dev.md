## Local Dev with Moov

Running all of Moov's services locally lets you write code against our services faster and let's us fix bugs faster.

Before starting please make sure you have Go setup [and can build our projects from source](https://github.com/moov-io/ach#from-source).

Once you're setup, run each service locally. This requires 4 terminals / shells:

```
# ACH
$ go run ./cmd/server/
ts=2018-12-13T19:18:10.340963Z caller=main.go:69 startup="Starting ach server version v0.6.0-rc2"
ts=2018-12-13T19:18:10.341843Z caller=main.go:122 transport=HTTP addr=:8080
ts=2018-12-13T19:18:10.34192Z caller=main.go:112 admin="listening on :9090"

# Auth
$ go run .
ts=2018-12-13T19:18:11.062095Z caller=main.go:80 startup="Starting auth server version v0.4.3-dev"
ts=2018-12-13T19:18:11.062633Z caller=main.go:103 main="sqlite version 3.25.2"
ts=2018-12-13T19:18:11.062617Z caller=main.go:92 admin="listening on :9091"
ts=2018-12-13T19:18:11.064059Z caller=sqlite.go:96 sqlite="starting database migrations..."
ts=2018-12-13T19:18:11.064153Z caller=sqlite.go:105 sqlite="migration #0 [create table if not exists users(user_id...] changed 0 rows"
... (more database migration log lines)
ts=2018-12-13T19:18:11.064345Z caller=sqlite.go:108 sqlite="finished migrations"
ts=2018-12-13T19:18:11.066804Z caller=main.go:189 transport=HTTP addr=:8081

# Paygate
$ go run .
ts=2018-12-13T19:18:11.970293Z caller=main.go:55 startup="Starting paygate server version v0.1.0-rc3"
ts=2018-12-13T19:18:11.970391Z caller=main.go:59 main="sqlite version 3.25.2"
ts=2018-12-13T19:18:11.971777Z caller=database.go:88 sqlite="starting database migrations"
ts=2018-12-13T19:18:11.971886Z caller=database.go:97 sqlite="migration #0 [create table if not exists customers(cus...] changed 0 rows"
... (more database migration log lines)
ts=2018-12-13T19:18:11.97221Z caller=database.go:100 sqlite="finished migrations"
ts=2018-12-13T19:18:11.974316Z caller=main.go:96 ach="Pong successful to ACH service"
ts=2018-12-13T19:18:11.975093Z caller=main.go:155 transport=HTTP addr=:8082
ts=2018-12-13T19:18:11.975177Z caller=main.go:124 admin="listening on :9092"

# OFAC
$ go run ./cmd/server/
ts=2019-02-21T16:56:29.655Z caller=main.go:42 startup="Starting ofac server version v0.5.1-dev"
ts=2019-02-21T16:56:29.655123Z caller=main.go:55 main="sqlite version 3.25.2"
ts=2019-02-21T16:56:29.65678Z caller=sqlite.go:73 sqlite="starting database migrations"
ts=2019-02-21T16:56:29.656886Z caller=sqlite.go:83 sqlite="migration #0 [create table if not exists customer_name...] changed 0 rows"
... (more database migration log lines)
ts=2019-02-21T16:56:29.657435Z caller=sqlite.go:87 sqlite="finished migrations"
ts=2019-02-21T16:56:29.657912Z caller=download.go:74 download="Starting refresh of OFAC data"
ts=2019-02-21T16:56:29.658027Z caller=main.go:103 admin="listening on :9094"
ts=2019-02-21T16:56:30.499764Z caller=download.go:117 download="Finished refresh of OFAC data"
ts=2019-02-21T16:56:30.502639Z caller=main.go:125 main="OFAC data refreshed - Addresses=11770 AltNames=9743 SDNs=7437"
ts=2019-02-21T16:56:30.503054Z caller=main.go:158 transport=HTTP addr=:8084
```

OPTIONAL:

Once all services are running you can use our `apitest` tool to ensure everything is working as intended.

```
# Disable Go Modules to install at $GOPATH/bin/apitest
$ GO111MODULE=off go get -u github.com/moov-io/api/cmd/apitest

# Run apitest and hit local services
$ apitest -local
2018/12/13 19:21:54.118542 main.go:46: Starting apitest v0.4.3-dev
2018/12/13 19:21:54.118573 main.go:61: Using http://localhost as base API address
2018/12/13 19:21:54.118585 main.go:83: Using X-Request-ID: 98d9d606167f03e6493c1dd09c22f085d8af2ea5
2018/12/13 19:21:54.121004 main.go:190: ACH PONG
2018/12/13 19:21:54.122041 main.go:200: auth PONG
2018/12/13 19:21:54.123022 main.go:210: paygate PONG
2018/12/13 19:21:54.253023 main.go:97: SUCCESS: Created user c2137a0a4b0e437b83c3786827ae8ef1be8f7bc7 (email: nervous.mirzakhani43@example.com)
2018/12/13 19:21:54.254055 main.go:106: SUCCESS: Cookie works for user c2137a0a4b0e437b83c3786827ae8ef1be8f7bc7
2018/12/13 19:21:54.256138 main.go:112: SUCCESS: Created OAuth access token, expires in 2h0m0s
2018/12/13 19:21:54.262281 main.go:127: SUCCESS: Created Originator Depository (id=7d9132b2f5d1e0f325540e48886817319a801c92) for user
2018/12/13 19:21:54.264103 main.go:134: SUCCESS: Created Originator (id=e4f63ed5efba7386c654cb14dd23ae53aa705cec) for user
2018/12/13 19:21:54.269265 main.go:142: SUCCESS: Created Customer Depository (id=2ee898f9663a3683860449abd36007d6fa241c2c) for user
2018/12/13 19:21:54.271595 main.go:149: SUCCESS: Created Customer (id=f01861ddaa466f33dfcde1600472dcefad8f1739) for user
2018/12/13 19:21:54.284106 main.go:156: SUCCESS: Created USD 216.76 transfer (id=54fa8e9e045f3a0e70de4ae28e47d1712eac413d) for user
2018/12/13 19:21:54.284716 main.go:162: SUCCESS: invalid login credentials were rejected
```

We support a similar `ofactest` tool to verify an OFAC instance is working as expected.

```
# Disable Go Modules to install at $GOPATH/bin/ofactest
$ GO111MODULE=off go get -u github.com/moov-io/ofac/cmd/ofactest

# Run ofactest and hit local services
$ ofactest -local
2019/02/21 16:58:18.777244 main.go:57: Starting moov/ofactest v0.5.1-dev
2019/02/21 16:58:18.777302 main.go:83: [INFO] using http://localhost:8084 for address
2019/02/21 16:58:18.784140 main.go:101: [SUCCESS] ping
2019/02/21 16:58:18.787780 main.go:108: [SUCCESS] last download was: 2s ago
2019/02/21 16:58:18.794475 main.go:121: [SUCCESS] name search passed, query="alh"
2019/02/21 16:58:18.800519 main.go:135: [SUCCESS] added company=21206 watch
2019/02/21 16:58:18.804408 main.go:143: [SUCCESS] alt name search passed
2019/02/21 16:58:18.808354 main.go:148: [SUCCESS] address search passed
```

Great! If you want to hit multiple services outisde of `apitest` use our [`local.Transport`](https://godoc.org/github.com/moov-io/api/cmd/apitest/local#Transport) to route requests to each local app.
