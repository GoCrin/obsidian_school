# Installation

MongoDB via docker installieren und ausführen.
```shell
sudo docker run -it --network host mongo
```

Mongo Shell über AUR installieren.
```shell
yay mongosh
```

# Mongosh

Mongosh schließen
```
exit
```

Alle Datenbanken anzeigen
```
show dbs
```

Aktuelle Datenbank anzeigen
```
db
```

Datenbank erstellen / verwenden
wird erst angezeigt, wenn auch Daten darin gespeichert worden sind
```
use datenbank
```

Datenbank löschen
```
db.dropDatabase('tutorial')
```

---

Quellen:
* [gersto github 25.02.2026](https://github.com/gersto/dbs/blob/main/mongoDB.md)
* [w3schools 25.02.2026](https://www.w3schools.com/mongodb/index.php)
* [docker mongo 25.02.2026](https://hub.docker.com/_/mongo)