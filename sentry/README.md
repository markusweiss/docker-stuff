# Sentry auf Docker installieren

## Vorbereitung:

_.env_ Datei anlegen

    SENTRY_POSTGRES_HOST=db
    SENTRY_POSTGRES_PORT=5432
    SENTRY_DB_USER=sentry
    SENTRY_DB_PASSWORD=secret
    SENTRY_REDIS_HOST=redis
    SENTRY_REDIS_PORT=6379
    SENTRY_SECRET_KEY=***SENTRY_SCHLUESSEL***

_docker-compose.yml_ Datei anlegen

    version: '3'
    services:
    sentry:
        container_name: sentry
        image: sentry
        env_file:
        - .env
        ports:
        - '9000:9000'
        depends_on:
        - db
        - redis
        tty: true
        stdin_open: true
    cron:
        container_name: sentry-cron
        image: sentry
        command: run cron
        env_file:
        - .env
        depends_on:
        - db
        - redis
    worker:
        container_name: sentry-worker
        image: sentry
        command: run worker
        env_file:
        - .env
        depends_on:
        - db
        - redis
    redis:
        container_name: sentry-redis
        image: redis
        volumes:
        - redis-data:/data
        ports:
        - '6379:6379'
    db:
        container_name: sentry-postgres
        image: postgres
        environment:
        POSTGRES_USER: sentry
        POSTGRES_PASSWORD: secret
        volumes:
        - pg-data:/var/lib/postgresql/data
        ports:
        - '5432:5432'
    volumes:
    redis-data:
    pg-data:

__secret-key__ auf Kommandozeile anlegen

    $ docker-compose run --rm sentry config generate-secret-key
    $ vi oder nano .env

danach den SENTRY_SECRET_KEY in der _.env_ Datei einfügen (austauschen) (***SENTRY_SCHLUESSEL***) und die compose Datei starten.


    
    
    $ docker-compose run --rm sentry upgrade
    $ docker-compose up -d


## Sentry starten


http://localhost:9000

---
Letzte Änderung: 27.02.2019