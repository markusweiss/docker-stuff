# Drupal Probleme

## Im Wartungsmodus kann sich nicht mehr eingelogged werden

nachdem die Seite im Wartungsmodus war konnte sich nicht mehr eingelogged werden.
 
## Lösung

auf der Konsole oder Adminer folgendes SQL Upate machen:

    UPDATE key_value SET value = "i:0;" WHERE collection = "state" AND name = "system.maintenance_mode"


[zurück](README.md)