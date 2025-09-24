# Installation

## Linux

```Bash
sudo pacman -S postgresql
sudo su - postgres
initdb -D /var/lib/postgres/data
exit
sudo systemctl start postgresql
sudo systemctl status postgresql
```

## Windows

# Konfiguration

## Linux

So gut wie jede Interaktion mit Postgresql wird über den `postgres` User durchgeführt. Auf diesen wechselt man mit folgendem Befehl

```Bash
sudo su - postgres
```

### DB Nutzer erstellen

Hier wird ein "Admin" erstellt

```Bash
createuser --interactive
```

* name of role -> root
* is superuser -> y

# Nutzung
## Postgresql starten

```Bash
sudo systemctl start postgresql
```

## Auf postgres user wechseln

```Bash
sudo su - postgres
```

## Datenbank erstellen

Als `postgres` user
```Bash
createdb myDatabaseName
```

## Mit Datenbank verbinden

Als `postgres` user
```Bash
psql -d myDatabaseName -h <hostname> -U <User>
```
`-U` ist im lokalen Linux betrieb sinnlos

## häufige Datenbank aufgaben

Diese werden innerhalb der `psql` shell ausgeführt

| Beschreibung                       | Befehl          |
| ---------------------------------- | --------------- |
| Liste der Datenbanken              | `\l`            |
| Mit Datenbank verbinden            | `\c <database>` |
| Tabellen Info                      | `\dt`           |
| Nutzer mit Berechtigungen anzeigen | `\du`           |

# Aufgaben

## Administration

### Schema anlegen
### Tabellen im Schema anlegen
### Rollen definieren
<u>Rolle für Schreiben</u>
<u>Rolle für Lesen</u>
### Berechtigungen für die Rollen im Schema auf die Tabellen verbergen
### Benutzer anlegen und den Rollen zuweisen
### Testen der User

![[nachweis_image.png]]
