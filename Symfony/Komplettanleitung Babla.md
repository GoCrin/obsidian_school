
[Symfony docs](https://symfony.com/doc/current/index.html)
# Installation

Um einen lokalen Web-Server für dieses Projekt zu starten werden folgende Schritte empfohlen.

## Windows

  

Das Repository clonen

  

```

git clone git@it.htl-hl.ac.at:220169/BablaNet.git

```

  

Scoop installieren (in Powershell)

```

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression

```

[Composer](https://getcomposer.org/Composer-Setup.exe) installieren

  

Symfony installieren (in Powershell)

  

```

scoop install symfony-cli

```

In das Projektverzeichniss wechseln und Abhängigkeiten via composer installieren

```

cd BablaNet

composer install

```

als nächstes muss **Docker installiert** werden. Dafür empfiehlt sich [Docker-Desktop](https://docs.docker.com/desktop/setup/install/windows-install/).

  

Nun Muss im Projekt-Verzeichniss die Datei `.env.dev.local` erstellt werden. In ihr muss diese Zeile stehen.

```

DATABASE_URL="mysql://<user>:<passwort>@127.0.0.1:3306/babladb?serverVersion=5.7.24&charset=utf8"

```

  

Aktiviere nun die PDO_mysql extension. Dafür führe diesen Befehl aus.

```

php --ini

```

  
  

Öffne die im Befehl zurückgegebene Datei und lösche das Semikolon (`;`) vom Anfang der folgenden Zeile

  

```

;extension=pdo_mysql

```

  

Nun muss die Datenbank eingerichtet werden.

```

php bin/console doctrine:database:create

```

  

## Docker

* Docker Desktop starten und den Installationsanweisungen folgen.

* `docker-compose up` im Projekt-Verzeichniss

* In der Docker Desktop app das Projekt aus wählen und alle programme bis auf `mercure` wieder stoppen.

## Datenbank

* Hierfür ist eine **gestartete Datenbank notwendig**.

* erstelle im Projekt-Root die Datei `.env.dev.local` und schreibe diese Zeile hinein (`<user>` und `<password>` müssen ersetzt werden. Alles andere darf ersetzt werden)

```
DATABASE_URL="mysql://<user>:<password>@127.0.0.1:3306/babladb?serverVersion=5.7.24&charset=utf8"
```

* die Datenbank die angeben wurde kann (wenn sie noch nicht existiert) mit diesem Befehl erstellt werden

```
php bin/console doctrine:database:create
```

* Nun müssen die Tabellen mit dem folgenden Befehl in der Datenbank erstellt werden

```
php bin/console doctrine:migrations:migrate
```

# Symfony-Webserver starten

* Wenn diese Anleitung funktioniert muss nur noch der Webserver gestartet werden

```
symfony server:start --no-tls
```