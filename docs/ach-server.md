## Running Moov ACH Server

The [Moov ACH Project](https://github.com/moov-io/ach) offers an HTTP Server for REST based ACH file construction, validation and tabulation. Any language which can use HTTP and JSON can use the ACH Server.

### Getting Started

First, you should be familiar with [Docker](https://docs.docker.com/get-started/) as that's the primary format for running the Moov ACH Server.

Second, find the [latest release on Docker Hub](https://hub.docker.com/r/moov/ach/tags/).

#### Running ACH Server on a local Docker host

To run the ACH Server locally simply run:

```
$ docker run moov/ach:v0.5.0 # Use the latest released version
ts=2018-12-11T23:36:22.0301927Z caller=main.go:65 startup="Starting ach server version v0.5.0"
ts=2018-12-11T23:36:22.0319685Z caller=main.go:118 transport=HTTP addr=:8080
ts=2018-12-11T23:36:22.0321508Z caller=main.go:108 admin="listening on :9090"
```

Then, (in a new terminal/shell) you can start making HTTP requests towards the ACH Server:

```
$ curl http://localhost:8080/ping
PONG

$ curl http://localhost:8080/files
{"files":[],"error":null}
```

We have posted [Ruby](https://github.com/moov-io/ruby-ach-demo) and [Go](https://github.com/moov-io/ach/blob/master/examples/http/main.go) HTTP examples for creating an entire ACH file.

#### Running ACH Server on Kubernetes

The following snippet runs the ACH Server on [Kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/) in the `apps` namespace. You could reach the ach instance at the following URL from inside the cluster.

```
# Needs to be ran from inside the cluster
$ curl http://ach.apps.svc.cluster.local:8080/ping
PONG

$ curl http://localhost:8080/files
{"files":[],"error":null}
```

Kubernetes manifest - save in a file (`ach.yaml`) and apply with `kubectl apply -f ach.yaml`.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: apps
---
apiVersion: v1
kind: Service
metadata:
  name: ach
  namespace: apps
spec:
  type: ClusterIP
  selector:
    app: ach
  ports:
    - name: http
      protocol: TCP
      port: 8080
      targetPort: 8080
    - name: metrics
      protocol: TCP
      port: 9090
      targetPort: 9090
---
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: ach
  namespace: apps
  labels:
    app: ach
spec:
  replicas: 1
  selector:
    matchLabels:
      app: ach
  template:
    metadata:
      labels:
        app: ach
    spec:
      containers:
      - image: moov/ach:v0.5.0
        imagePullPolicy: Always
        name: ach
        ports:
          - containerPort: 8080
            name: http
            protocol: TCP
          - containerPort: 9090
            name: metrics
            protocol: TCP
        resources:
          limits:
            cpu: 0.1
            memory: 25Mi
          requests:
            memory: 10Mi
        readinessProbe:
          httpGet:
            path: /ping
            port: 8080
          initialDelaySeconds: 5
          periodSeconds: 5
        livenessProbe:
          httpGet:
            path: /ping
            port: 8080
          initialDelaySeconds: 5
          periodSeconds: 5
      restartPolicy: Always
```
