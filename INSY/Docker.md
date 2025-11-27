```Bash
docker run postgresql
```

Lädt ein app image vom docker hub herunter, sammelt alles was dieses Programm braucht und startet dann die Applikation in Form eines Containers. Der Vorteil den Docker über einer virtuellen Maschine hat ist, dass Docker die Programme in Containern fast mit der gleichen Geschwindigkeit ausführt wie ein nicht virtualisiertes Programm

## Port mapping ( / forwarding)

```Bash
docker run postgresql -p 5432:3232
```

# Wichtige Befehle

| Befehl                              | Beschreibung                                                                                                                          |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `docker pull NAME:VERSION`          | Image (von [dockerhub](https://hub.docker.com/)) herunterladen. Version kann auf dockerhub bei einem Image unter Tags gefunden werden |
| `docker ps [-a]`                    | (-a für alle / history) Container anzeigen                                                                                            |
| `docker images` / `docker image ls` | anzeigen alle heruntergeladenen Images                                                                                                |
| `docker run [--name]`               | Aus Image einen rennenden Container machen (ausführen). `--name` um einen namen zu setzen                                             |
| `docker start`                      | Bereits erstellten container ausführen                                                                                                |
# Docker image erstellen

Baut ein Docker-Image

```bash
docker build -f Dockerfile -t cool-debian:latest .
```

Dieses Image brauch ein Ausgangs-Image, dies gibt man mit `FROM` an

```Dockerfile
FROM [Image]:[tag]
RUN apt-get update
RUN apt-get install -y libpq-dev
COPY [source] [target]

# Ausführbare Datei
CMD ["executable", "param1", "param2"]

# Command in einer shell ausführen - /bin/sh -c
CMD command param1 param2
```
