Symfony verwendet ein "Programm", dass sich Doctrine nennt. In folgenden Schritten wird dieses Programm installiert und konfiguriert um einen Datenbank auf localhost zu erstellen
### Doctrine installieren

```
composer require symfony/orm-pack
composer require --dev symfony/maker-bundle
```


### Doctrine konfigurieren

im Projekt unter `./config/packages/doctrine.yaml` wird in doctrine:dbal: folgende Zeilen eingefügt

```
doctrine:
	dbal:
		driver: 'pdo_mysql'
		server_version: '5.7.24'
		charset: utf8mb4
		host: 127.0.0.1
		port: 3306
		user: '%env(DATABASE_USER)%'
		password: '%env(DATABASE_PWD)%'
		dbname: '%env(DATABASE_NAME)%'
		profiling_collect_backtrace: '%kernel.debug%'
		use_savepoints: true
```


Im `./.env`

```
DATABASE_USER="root"
DATABASE_PWD="root"
DATABASE_NAME="messprototyp"
```


Finde nun mit diesem Befehl deine von php geladene Konfigurationsdatei

```
php --ini
```


In der oben gefundenen Datei (`php.ini`) wird ein `;` entfernt. Suche dafür in deinem Editor nach folgender Zeile und entferne das 1. Zeichen.

```
;extension=pdo_mysql
```


Nun ist alles konfiguriert und Befehle wie folgender sollten fehlerfrei ablaufen. Dieser Befehl erstellt die im `.env` eingestellte Datenbank ("messprototyp")

```
php bin/console doctrine:database:create
```
