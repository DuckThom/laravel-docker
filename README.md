# laravel-docker
A basic docker-compose config for Laravel (and probably other things as well)

## Components

- nginx
- php-fpm 7.1 with xdebug and blackfire
- mysql 5.7

## Storage

Laravel installation: `app`

Mysql data: `mysql/data`

## Setup

- Set domain name in `docker-compose.yml`.
- Change PHP extensions in `php/Dockerfile` if necessary.

### nginx-proxy

If you are using [nginx-proxy](https://github.com/jwilder/nginx-proxy), use the `0.1` tag make sure the external_name setting matches the name of the network used by the nginx-proxy container.

### Traefik

If you are using [traefik](https://traefik.io), check if the external network name is correct and change the labels of the webserver container if necessary.
