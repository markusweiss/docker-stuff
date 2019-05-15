# Shortcuts auf der Kommandozeile:

+ das sind alles Beispiele für meinen persönlichen Gebrauch.
+ Kein Anspruch auf Richtigkeit.
+ Auch die Dokumentation ist nur rudimentär.

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

---
Letzte Änderung: 23.12.2018  