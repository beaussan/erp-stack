# Erp stack

This is the running stack for the Erp project

See :
- [Front end](https://github.com/beaussart/erp-front)
- [Back end](https://github.com/beaussart/erp-back)

There is two ways of running this stack :
- using local ports (by default, `3030` for the server and `8090` for the ui)
- using local domains (by default, `back.erp.localhost` and `erp.localhost`) using the port 80

## Creating an account

To create an account, you should do :

using the port version

```bash
$ curl curl -d '{"email": "foo@bar.fr", "firstName": "foo", "lastName": "bar", "password": "azerty" }' -H 'Content-Type: application/json' http://localhost:3030/auth/register
```

using the domain version

```bash
$ curl curl -d '{"email": "foo@bar.fr", "firstName": "foo", "lastName": "bar", "password": "azerty" }' -H 'Content-Type: application/json' http://back.erp.localhost/auth/register
```

## Requirements

This projects is using docker and docker-compose.

## Runing local domains

This is using [Traefik](https://traefik.io/) as a reverse proxy for urls.

To run this stack, you have to do the following command : 
```bash
docker-compose up -d
```

To change the urls (like a domain pointing to the server), you have to :
- change the server url in the `docker-compose.yml` file (line 40)
- change the client url in the `docker-compose.yml` file (line 55)
- change the config for the client in the `front-config/traefik.json` to set the new server url


## Running with ports

To run this stack, you have to do the following command :
```bash
docker-compose -f docker-compose.local.yml up -d
```

It will, by default expose the front end on the `8090` port and the server on the `3030` port.

To change the ports, you have to :
- change the server port in the `docker-compose.local.yml` file (line 21)
- change the client port in the `docker-compose.local.yml` file (line 43)
- change the config for the client in the `front-config/local.json` to set the new server url
