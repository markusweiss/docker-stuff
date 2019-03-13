# Sentry auf Docker installieren

## Vorbereitung:

_.env_ Datei anlegen

    SENTRY_POSTGRES_HOST=db
    SENTRY_POSTGRES_PORT=5432
    SENTRY_DB_USER=sentry
    SENTRY_DB_PASSWORD=secret
    SENTRY_REDIS_HOST=redis
    SENTRY_REDIS_PORT=6379
    SENTRY_SECRET_KEY=[sentry-schluessel]

    SENTRY_EMAIL_HOST=[smtp.meinmailprovider.de]
    SENTRY_EMAIL_PORT=587 
    SENTRY_EMAIL_PASSWORD=[emailpasswort]
    SENTRY_EMAIL_USER=[username-von-mailaccount]
    SENTRY_EMAIL_USE_TLS=true 
    SENTRY_SERVER_EMAIL=[meine.mail@meinmailprovider.de]

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

__Mail konfigurieren__ auf Kommandozeile anlegen

    $ vi oder nano .env

Die in Klammern [meinwert] geschrieben Werte durch Eure Einstellungen ersetzen. 

Das sind in der Regel die Daten mit denen Ihr auch Eure Mails abruft.

Ich würde für die Sentry Konfiguartion eine neues Konto anlegen.

__secret-key__ auf Kommandozeile anlegen

    $ docker-compose run --rm sentry config generate-secret-key
    $ vi oder nano .env

danach den SENTRY_SECRET_KEY in der _.env_ Datei einfügen (austauschen) [sentry-schluessel] und die compose Datei starten.

    $ docker-compose run --rm sentry upgrade
    $ docker-compose up -d


## Sentry starten


http://localhost:9000

---
Letzte Änderung: 13.03.2019