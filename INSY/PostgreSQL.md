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

### DB erstellen


```Bash
createdb myDatabaseName
```
