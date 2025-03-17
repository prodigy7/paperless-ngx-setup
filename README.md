# Paperless NGX Docker Setup

## Setup

For setup a full featured paperless ngx docker setup, follow this steps:

1. Copy `docker-compose.env.dist` to `docker-compose.env`
2. Generate a random string with `openssl rand -hex 64` and set result to `PAPERLESS_SECRET_KEY`
3. Copy `.env.dist` to `.env`
4. Generate a random string with `openssl rand -hex 64` and set result to `PAPERLESS_DBPASS`
5. Change `PAPERLESS_ROOT_DIR` and `PAPERLESS_CONSUME_DIR` to your requirements.
6. Maybe you have to change `DOCKER_*_VERSION` to current published versions
7. Then execute the following commands directly one after the other in the shell:
    1. `source .env`
    2. `sudo mkdir -p ${PAPERLESS_ROOT_DIR}/redis`
    3. `sudo chmod 777 ${PAPERLESS_ROOT_DIR}/redis`

## Running

Run `docker compose pull`. This will pull the image from the GitHub container registry.
After that you can start the container with `docker compose up -d`.

To be able to login, you will need a "superuser". To create it, execute the following command:

```bash
docker compose run --rm webserver createsuperuser
```

## Commands

Here you will find a list of available commands: https://docs.paperless-ngx.com/administration/

