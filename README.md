# Setup Guide

## Setting up NGINX config with 

Edit default.conf to add proxy routes.

Ex: Re-routing to google.com.
```conf
location /google {
    rewrite ^/google(.*) /$1 break;
    proxy_pass https://www.google.com;
}
```

## Running Application Locally Through Docker

### 1. In terminal, change to repo's root directory

### 2. Build Docker Image

This example names the built image as "reverse proxy".

```sh
docker image build -t reverse-proxy .
```

### 3. Run Docker Container

This example runs a docker container with name "app-name" using the image built 
in step 2 named "reverse-proxy". It exposes port 8080 locally and maps 
it to port 80 of the docker container which the NGINX server is listening to.

```sh
docker container run  --name app-name -p 8080:80 -d reverse-proxy
```