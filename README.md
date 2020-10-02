# docker-adaptauthoring

![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/3wordchant/adaptauthoring)

Authoring SCORM-compatible training using the [Adapt Authoring](https://github.com/adaptlearning/adapt_authoring) tool.

## How to use this image

Because Adapt requires a database to run, the easiest way to get started is to use `docker-compose` to set up Adapt and MongoDB automatically.

Fetch the example `docker-compose.yml`:

    wget https://github.com/3-w-c/docker-adaptauthoring/blob/master/docker-compose.yml

Edit the variables under `services.app.environment`, then push the button!

    docker-compose up

## Environment variables

You can configure Adapt's initial set-up using these variables:

- `DOMAIN` - hostname for the Adapt service
- `PORT` (default `5000`) - TCP port for the Adapt service
- `DB_HOST` - MongoDB server hostname
- `DB_USER` - MongoDB username
- `DB_NAME` - MongoDB database name
- `SESSION_SECRET` - HTTP session secret key (set to something random)
- `ADMIN_EMAIL` - email address for the default superuser account
- `ADMIN_PASSWORD` - password for the default superuser account
- `FROM_EMAIL` - `From:` email address for notifications

## Docker secrets

As well as environment variables, you can also load `SESSION_SECRET` and
`ADMIN_PASSWORD` from files, which is helpful if want to keep secret data in
[Docker swarm mode secrets](https://docs.docker.com/engine/swarm/secrets).

Simply set `SESSION_SECRET_FILE` / `ADMIN_PASSWORD_FILE`.
