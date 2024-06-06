# Temporal Java GRPC Proxy

A proxy for forwarding requests to Temporal. This proxy handles mTLS on behalf of Temporal clients.

Code is largely reused under Apache 2 from the [grpc/grpc-java](https://github.com/grpc/grpc-java/tree/master) project, specifically [this example](https://github.com/grpc/grpc-java/blob/master/examples/src/main/java/io/grpc/examples/grpcproxy/GrpcProxy.java).

## Requirements

*(AKA What I had installed)*

* Java 1.8+

## Usage

* Set the following envinroment variables;
  * `TEMPORAL_HOST=<namespace>.<account_id>.tmprl.cloud`
  * `TEMPORAL_PORT=<>` (Defaults to `7233`)
  * `TEMPORAL_TLS_KEY_PATH` (Client key for mTLS)
  * `TEMPORAL_TLS_CERT_PATH` (Client cert for mTLS)

* `./gradlew run` - starts the proxy server on port `9891`.

* Configure your Temporal client to use the address of the proxy (`127.0.0.1:9891`, ensure the namespace matches what has been set in the proxy's host configuration, and _don't_ configure certificates/mTLS in your client).
* Run your client.

## Learn more about Temporal and the Java SDK

* [Temporal Hompage](https://temporal.io/)
* [Temporal Java SDK Samples](https://github.com/temporalio/samples-java)
* [Java SDK Guide](https://docs.temporal.io/dev-guide/java)