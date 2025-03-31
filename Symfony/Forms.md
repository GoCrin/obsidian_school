Scheinbar bietet das Symfony-Framwork eine einfache Methode Formulare zu generieren. Hierfür muss folgendes Composer-Package installiert werden

```
composer require symfony/form
```


In der Symfony-Dokumentation wird folgender empfohlener Workflow beschrieben: 
* Ein Formular mit Controller oder einer eigenen Formularklasse bauen
* Erstelle eine Vorlage (.twig) für den Nutzer
* Verarbeite die erhaltenen Daten

