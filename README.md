# nginx-rproxy

This builds on the official nginx-alpine image and adds the ability to accept configuration information via environment variables (using envsbt).

This instance of nginx acts as a reverse proxy, accepting HTTP connections on port 80 and sending them on to a backend service.

On Docker Hub https://hub.docker.com/r/richardjkendall/nginx-rproxy

On GitHub https://github.com/richardjkendall/nginx-rproxy

## Configuration

Expects the following environment variables to be defined

| Variable | Purpose |
|---|---|
|BACKEND_SCHEME|What URL scheme to use for the backend service, typically http or https|
|BACKEND_HOST|Host name or IP address of the backend service|
|BACKEND_PORT|Port number for the backend service|

## Running

Example to get this running (runs in the foreground)

```sh
docker run --rm \
-e BACKEND_SCHEME=https \ 
-e BACKEND_HOST=backend.service.com \ 
-e BACKEND_PORT=8000 \
-p 8080:80 \ 
richardjkendall/nginx-rproxy
```

This will run an instance which forwards connections to localhost on port 8080 to https://backend.service.com:8000
