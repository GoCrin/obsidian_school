Apache2

Man brauch zum Aufrufen eines Webservers einen Browser

https:// ip

Webserver liefert html. Selbst wenn php verwendet wird, wird diese zu html kompiliert

`apt install apache2`

nginx
IIS


Es ist möglich mehrere Webseiten auf einem Webserver rennen zu lassen.

### Für Apache

`cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/001-seite1.conf`

in diesem file den port auf 81 und document root auf /var/www/seite 1

`cd /var/www `
`mkdir seite1`
`touch index.html`

a2ensite
a2dissite

`nvim /etc/apache2/ports.conf
	`Listen 81


lynx ip