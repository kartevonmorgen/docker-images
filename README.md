# Frontend and Backend Server for Docker

ONLY FRONTEND WORKS!

The frontend and backend for [Karte von morgen](https://github.com/kartevonmorgen/kartevonmorgen/) is based on the documentation [Open Fair DB](https://github.com/kartevonmorgen/openfairdb) and [Karte von morgen](https://github.com/kartevonmorgen/kartevonmorgen.ts)


## Dependencies
* [Docker](https://docs.docker.com/get-docker/)
* [Docker Compose](https://docs.docker.com/compose/install/)

## Quick start

You can remove *labels* and *networks* - we are using Traefik as Reverse Proxy with http3 enabled.

If you want to use the network *web*, you can create it with
```sh
docker network create web
```

### Step 1

Clone this repo and start it with
```sh
docker-compose up -d
```
The images were build local with the Dockerfiles.

## Volumes

### Backend
Docker Compose uses a local folder as storage for the backend database at ./data/openfairdb/ which points to /var/openfairdb

## Ports

### Frontend
The Frontend uses Port 3000 [PROD] or 3001 [DEV]

### Backend
The backend uses Port 8000 which is forwarded to 6767.

## Logging

```sh
docker-compose logs -f --tail=10000 #last 10000 lines
```

## License

Copyright (c) 2021 [Reiner Hosting und Webdesign](https://www.alexreiner.de)

This project is licensed under the AGPLv3 license.