## Introduction
This is a docker-compose file to build Graylog 2

## Git repository
The source files for this project can be found here: https://github.com/taladocker/graylog

## Running

Create new docker-compose config *docker-compose.prod.yml*

```
graylog:
  environment:
    GRAYLOG_PASSWORD_SECRET: password
    GRAYLOG_ROOT_PASSWORD_SHA2: password-sha2
    GRAYLOG_REST_TRANSPORT_URI: http://ip-address:12900
```

Start service by run the following

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```