## Scoop installieren

Starte die PowerShell und führe folgende Befehle aus um das Programm "scoop" zu installieren. Dieses Programm wird verwendet um die "symfony-cli" zu installieren.

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

## Composer installieren

Installiere den "Paket-Manager" von PHP mit diesem Link
https://getcomposer.org/Composer-Setup.exe

## Symfony-cli installieren

Die symfony-cli wird mit dem bereits installiertem scoop heruntergeladen

```
scoop install symfony-cli
```


## Projekt erstellen

Bevor nun das Projekt erstellt wird sollte man folgenden Befehl verwenden um zu sehen ob symfony korrekt installiert wurde

```
symfony check:requirements
```

Wenn bis jetzt nichts Fehlgeschlagen hat, kann mit diesem Befehl ein Folder im Working-Directory erstellt werden in dem das Symfony-Projekt erstellt wird

```
symfony new my_project_directory --version="7.2.x" --webapp
```

### Webserver im dev-modus starten

Um jetzt das Projekt zu testen kann lokal ein Server gestartet werden. Dafür **muss** man sich natürlich **im Verzeichnis des Projekts befinden**.

```
cd my_project_directory
symfony server:start
```


