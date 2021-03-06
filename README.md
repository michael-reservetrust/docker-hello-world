[![Build Status](https://travis-ci.org/infrastructure-as-code/docker-hello-world.svg?branch=master)](https://travis-ci.org/infrastructure-as-code/docker-hello-world)

# infrastructureascode/hello-world

A [Prometheus](https://prometheus.io/)-instrumented Docker "Hello World" web server.

## Features

1. Always returns a HTTP 200 status code and a "Hello, World!" message at the `/` path.
1. Has a metrics endpoint at `/metrics` that returns Prometheus metrics.
1. Has a health check endpoint, `/health`, that returns an empty response and a HTTP 200 response.

## Building

```
docker build --rm -t infrastructureascode/hello-world .
```

## Usage

```
# start the container
docker run \
  --detach \
  --name hello-world \
  --publish 8000:8080 \
  infrastructureascode/hello-world

# curl the container
curl http://0.0.0.0:8000/

# curl the health check endpoint which returns an empty response
curl http://0.0.0.0:8000/health

# curl Prometheus metrics
curl http://0.0.0.0:8000/metrics
```
