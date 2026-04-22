## Virtuelles env
Ein Environment erstellen 
```Bash
python -m venv myvenv
```

dieses verwenden
```Bash
source myvenv/bin/activate
```

### Daseinsberechtigung

Virtuelle Umgebungen sind gut um ein ganzes Projekt an einem Punkt zu haben und teilen zu können. Durch virtuelle Umgebungen kann jede library und sogar der python Interpreter eines Projekts leicht geteilt werden.

## FastApi

Ist eine python library um eine web-api bereit zustellen. Ein einfaches Programm hat eine Funktion, die über einen `decorator` einer route zugewiesen wird.

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
async def root():
    return {"message": "Hello World"}
```

Dieses kann jetzt mit folgendem Befehl gestartet werden.
```bash
fastapi dev
```

oder wenn die Python-Datei nicht `main.py` heißt:

```bash
fastapi dev myFile.py
```

Pfadvariablen werden eingeklammert.
```python
@app.get("/date/{date}")
async def read_item(date):
    return fetch_nameday_by_date(date)
```

Abfrageparameter (`http://localhost/items/?skip=0&limit=10`) sind Funktionsparameter automatisch, wenn sie nicht im `decorator` genannt werden.

```python
@app.get("/name/")
async def read_item_by_name(name):
    return fetch_nameday_by_name(name)
```

## Data Faker
```bash
pip install faker
```

```python
from faker import Faker  
fake = Faker()
```