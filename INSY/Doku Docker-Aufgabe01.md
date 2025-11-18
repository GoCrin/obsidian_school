# Docker-Netzwerk

Ziel ist es folgendes Netzwerk auf zu bauen.

![[Pasted image 20251118211657.png]]

Der 1. Schritt in Richtung dieses Plans ist das Erstellen eines Docker-Netzwerks

```bash
sudo docker network create -d bridge aufgabe-net
```

# Projektgrundstruktur Webserver ohne Datenbank

```bash
mkdir docker-aufgabe01
cd docker-aufgabe01/
mkdir www
touch Dockerfile apache-config.conf ./www/index.php
```

in `Dockerfile`
```Dockerfile
FROM php:8.2-apache
COPY src/ /var/www/html/

RUN apt-get update && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo_pgsql pgsql
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
```

in `apache-config.conf`
```xml
<VirtualHost *:80>
  ServerAdmin me@mydomain.com
  DocumentRoot /var/www/site

  <Directory /var/www/site/>
      Options Indexes FollowSymLinks MultiViews
      AllowOverride All
      Order deny,allow
      Allow from all
  </Directory>

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```
in `www/index.php`
```php
<?php
echo "Hello World";
?>
```

# Webserver ausführen

```Bash
sudo docker build -t aufgabe-web .
sudo docker run --network=aufgabe-net -p 8080:80 -d --name web aufgabe-web
```

`ìndex.php` kann jetzt in einem Browser unter `http://localhost:8080/` aufgerufen werden.

# Projekt um Datenbank erweitern

```Bash
sudo docker pull postgres
sudo docker run --network=aufgabe-net -p 5432:5432 -d --name db-server -e POSTGRES_PASSWORD=postgres postgres
```
Hier muss die Umgebungsvariable `POSTGRES_PASSWORD` gesetzt werden da das docker image dies verlangt.

## SQL-Datei innerhalb des Postgres-Containers verwenden

Als 1. wird folgende `.sql`-Datei namens `aufgabe-postgres.sql` erstellt
```sql
CREATE TABLE people (
	firstname VARCHAR(255),
	lastname VARCHAR(255),
	age INT
);

INSERT INTO people (firstname, lastname, age) VALUES
	('Simon', 'Neissl', 17),
	('Simon', 'Koch', 17),
	('Simon', 'Falkner', 17);
```

Diese wird jetzt in den Container kopiert.
```bash
sudo docker cp aufgabe-postgres.sql db-server:/aufgabe-postgres.sql
```

Nun wird die Datenbank im Container erstellt

```bash
sudo docker exec -i -u postgres db-server createdb aufgabe-db
```

Jetzt muss nur noch der Befehl zur Verwendung der Datei innerhalb des Containers ausgeführt werden.

```bash
sudo docker exec -i db-server psql -U postgres -d aufgabe-db -f /aufgabe-postgres.sql
```

# Liste an Personen über Webserver anzeigen

`ìndex.php` wird dafür abgeändert
```php
<?php
echo "<table style='border: solid 1px black;'>";
echo "<tr><th>Id</th><th>Firstname</th><th>Lastname</th></tr>";

class TableRows extends RecursiveIteratorIterator {
  function __construct($it) {
    parent::__construct($it, self::LEAVES_ONLY);
  }

  function current() {
    return "<td style='width:150px;border:1px solid black;'>" . parent::current(). "</td>";
  }

  function beginChildren() {
    echo "<tr>";
  }

  function endChildren() {
    echo "</tr>" . "\n";
  }
}

$servername = "db-server";
$username = "postgres";
$password = "postgres";
$dbname = "aufgabe-db";

try {
  $conn = new PDO("pgsql:host=$servername;dbname=$dbname", $username, $password);
  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  $stmt = $conn->prepare("SELECT * FROM people");
  $stmt->execute();

  // set the resulting array to associative
  $result = $stmt->setFetchMode(PDO::FETCH_ASSOC);
  foreach(new TableRows(new RecursiveArrayIterator($stmt->fetchAll())) as $k=>$v) {
    echo $v;
  }
} catch(PDOException $e) {
  echo "Error: " . $e->getMessage();
}
$conn = null;
echo "</table>";
?>
```

Der Webserver wird jetzt (gestoppt und) gelöscht um ihn wie im Punkt "Webserver ausführen" mit der neuen Datei, neu zu erstellen.

```bash
sudo docker stop web
sudo docker rm web
sudo docker build -t aufgabe-web .
sudo docker run --network=aufgabe-net -p 8080:80 -d --name web aufgabe-web
```

# Ergebnis

Es wird jetzt (wie durch ein Wunder) der Inhalt der `people` Tabelle ausgegeben. 

![[Pasted image 20251118210143.png]]
# Quellen

* [www.w3schools.com: php](https://www.w3schools.com/php/)
* [docs.docker.com: network](https://docs.docker.com/engine/network)
* [hub.docker.com: php](https://hub.docker.com/_/php)
* [hub.docker.com: postgres](https://hub.docker.com/_/postgres)