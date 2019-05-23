# Shortcuts auf der Kommandozeile:

+ das sind alles Beispiele für meinen persönlichen Gebrauch.
+ Kein Anspruch auf Richtigkeit.
+ Auch die Dokumentation ist nur rudimentär.

## docker-compose.yml auf Richtigkeit prüfen

    $ docker-compose config

## docker-compose.yml starten

    $ docker-compose up

## docker-compose.yml stoppen

    $ docker-compose down

**Achtung auch DB Inhalte werden gelöscht falls sie im Container liegen**

## Container anzeigen

    $ docker ps

## Logs von Container anschauen (Beispiel)

    $ docker logs --follow cbd017bcbcf9

## Images auflisten

    $ docker image ls

## Image löschen

    $ docker rmi imageId

## Alle Docker Container stoppen

    $ docker stop $(docker ps -a -q)

## Alle Docker Container löschen


    $ docker rm -f $(docker ps -a -q)
    $ docker rmi -f $(docker images -q)


## Bestimmten Container Id mit bash starten (Beispiel)

    $ docker exec -it 270fbf77bea3 /bin/bash


## Docker Laufwerke (volume) prüfen

    docker volume inspect 1c45497569de94c95b896d319b2329f0228536dc585d84a45f5f5f7150c30fcd

## Nicht genutze Laufwerke bereinigen

    $ docker volume prune 
---
Letzte Änderung: 23.05.2019  