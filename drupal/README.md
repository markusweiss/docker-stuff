# Drupal 8 auf Docker installieren

hier vorab nur eine simple Installation zum schnellen Testen, wird noch bei Bedarf erweitert.

Ordner erstellen, z.B.: _Drupal8_

**docker-compose.yml** in den Ordner herrunterladen und danach auf der Konsole starten.

    $ cd Drupal8
    $ docker-compose up

Im Browser: [_localhost:8080_](http://localhost:8080) aufrufen.

Installation erfolgt dann per Drupal Installationsscript.

## Achtung

volumes: - /**datadir**:/var/lib/mysql

**Die Speicherung im Container wurde auf den lokalen Ordner _datadir_ gelegt. Somit gehen die Daten nicht verloren.**

## Hier Sammlung von aufgetreten Problemen:

* [Probleme Drupal](know-how-scripte.md)
