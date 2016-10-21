# laravel-docker
A basic docker-compose config for Laravel (and probably other things as well)

## Components

- nginx
- php-fpm 7.0
- mysql

## Storage

Laravel installation: `app`

Logs:
- nginx: `nginx/logs`

Mysql data: `mysql/data`

## Setup

- Set domain name in docker-compose.yml.
- Change PHP extensions in php/Dockerfile if necessary.
- When using [nginx-proxy](https://github.com/jwilder/nginx-proxy), make sure the external_name setting matches the name of the one used by nginx-proxy.
