# Befüllen der Datenbank

Die gegebene Datenbank heißt `dbperformance` und hat genau eine Tabelle namens `customers` mit den Spalten `name` und `address`.
Die Datenbank wird mittels Python-Script mit 1.000.000 Datensätzen befüllt.

```python
from faker import Faker  
import mysql.connector  
  
fake = Faker()  
numberOfEntries = 1_000_000  
  
mydb = mysql.connector.connect(  
 host="localhost",  
 user="root",  
 password="root",  
 database="dbperformance"  
)  
  
mycursor = mydb.cursor()  
  
sql = "INSERT INTO customers (name, address) VALUES (%s, %s)"  
  
for i in range(numberOfEntries):  
 val = (fake.name(), fake.address())  
 mycursor.execute(sql, val)  
  
mydb.commit()
```

Dieses Script braucht folgende 2 libraries um zu funktionieren.

```shell
pip install mysql-connector-python
pip install faker
```

# Analyse der Performance

Dieser Befehl dauert $371ms$.
```Mysql
SELECT * FROM customers;
```

Dieser dauert $274ms$.
```MySql
SELECT * FROM customers WHERE name LIKE 'Maria%';
```

# Index auf Name

```mysql
CREATE INDEX name_index ON customers (name); 
```

Dieser Befehl dauert jetzt $596ms$.
```Mysql
SELECT * FROM customers;
```

Und dieser dauert jetzt nur noch $32ms$.
```MySql
SELECT * FROM customers WHERE name LIKE 'Maria%';
```