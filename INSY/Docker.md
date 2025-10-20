```Bash
docker run postgresql
```

Lädt ein app image vom docker hub herunter, sammelt alles was dieses Programm braucht und startet dann die Applikation in Form eines Containers. Der Vorteil den Docker über einer virtuellen Maschine hat ist, dass Docker die Programme in Containern fast mit der gleichen Geschwindigkeit ausführt wie ein nicht virtualisiertes Programm

## Port forwarding
```Bash
docker run postgresql -p 4711:3232
```

