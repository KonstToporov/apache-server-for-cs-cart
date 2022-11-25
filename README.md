# Docker based development environment for CS-Cart:
- PHP versions: 7.4;
- MySQL 5.7;
- apache web server.

## Requirements
- Docker
- docker-compose

## Run the environment using docker:

```bash
  make up
```

## Run the interacitve bash of the server

```bash
  make bash
```

## Apache

The root directory `www`. So put the cs-cart files there.


## Sending e-mails

There is Mailhog included. So to catch the emails by mailhog setup the cs-cart store in admin panel. Go to `Settings -> E-mails` and setup next fields:

- `Method of sending e-mails:` -> `via SMTP server`
- `SMTP host` -> `127.0.0.1:1025`

## Database

All mysql data is stored in db_data folder. So it is persisted despite the state of containers.


### MySQL credentials:

Username: `root`

Password: `root`


## Result

- Apache web server available on localhost with ports 80 and 443.
- Mailhog web interface: http://localhost:8025/
- PhpMyAdmin web interface: http://localhost:8010/


## XDebug

XDebug configuration specifieced for php 7.4 in `configs/php7.4/docker-php-ext-xdebug.ini`
To setup it in VSCode install `PHP Debug` extension and specify for each store the next settings in `www/<app_name>/.vscode/launch.json`

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "type": "php",
            "request": "launch",
            "port": 9003,
            "pathMappings": {
                "/var/www/html/<app_name>": "${workspaceFolder}"
            }
        }
    ]
}
```