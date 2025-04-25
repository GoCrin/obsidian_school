## Steps to reproduce

1. erstelle ps1 Datei mit Inhalt

```
symfony server:start
Start-Process http://127.0.0.1:8000
```

2. führe dieses aus.
3. stoppe den symfony dev server mit STRG + C
4. Sieh Fehler wie diesen
```
remove C:\Users\linus\.symfony5\log\25dce057d68b675e750eec12a0aa24db7455a052.log:The process cannot access the file because it is being used by another process.
```

## Bereits versuchte Lösungen
* **.log Datei händisch löschen** -> nach Server start und ende wird neues .log erstellt welches von cli nicht gelöscht werden kann
* **Laptop neustarten**
* **mit ressourcenmonitor zugeordnete handles für file suchen**
* **jeden Prozess mit php schließen**

