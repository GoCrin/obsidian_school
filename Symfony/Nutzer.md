## neuen Nutzer erstellen

**Sollte** in der Datei `/composer.json` die **Zeile** `"symfony/security-bundle": "7.2.*"` **nicht vorhanden** sein, führe diesen Befehl aus

```
composer require symfony/security-bundle
```

Als nächstes erstelle einen Nutzer. Hierfür muss alles von [[Datenbankverbindung]] funktionieren.

```
php bin/console make:user
```

Obiger Befehl stellt viele Fragen. Diese können im Normalfall mit einem einfachen Enter beantwortet werden.

Nun wurde eine Datei `/src/Entity/User.php` erstellt. Jedoch existiert noch keine Tabelle in der Datenbank. diese wird mit Befehlen um eine Migration zu machen in die Datenbank geschrieben.

```
php bin/console make:migration
	php bin/console doctrine:migrations:migrate
```

## Login- & Registrierseite generieren

Führe diesen Befehl aus um eine Login Seite zu generieren

```
php bin/console make:security:form-login
```

