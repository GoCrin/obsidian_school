# Sprachen

- DDL (Data Definition Language)
- DML
- DQL
- DCL
- TCL

# Docker

```bash
sudo docker run --name insy-mysql --network host -e MYSQL_ROOT_PASSWORD=root -d mysql
```

```bash
mariadb -h 127.0.0.1 -P 3306 -u root -proot
```

# Union

[mysqltutorial](https://www.mysqltutorial.org/mysql-basics/mysql-union/)

# Case

[mysqltutorial](https://www.mysqltutorial.org/mysql-control-flow-functions/mysql-case-function/)

# Subquery

[mysqltutorial](https://www.mysqltutorial.org/mysql-basics/mysql-subquery/)

# Stored Procedures
[mysqltutorial](https://www.mysqltutorial.org/mysql-stored-procedure/)
# Window Functions
[mysqltutorial](https://www.mysqltutorial.org/mysql-window-functions/)

# Transactions

Schaut, das ein Befehl korrekt ausgeführt wurde, bevor der nächste Befehl ausgeführt wird. Wenn ein Befehl nicht funktioniert, wird autonom ein "rollback" gemacht. Bis der "commit" Befehl ausgeführt wurde sind die Änderungen durch Transactions nicht auf der Festplatte gespeichert, sondern nur in einem Zwischenspeicher.

