Konto1 ---------50€------> Konto2
-50 UPDATE                         UPDATE +50

Transaction über wacht Update1 und Update2 wenn beide OK sind werden die Ergebnisse erst in die Datenbank geschrieben (Write)

START TRANSACTION;
SELECT @A:=SUM(salary) FROM table1 WHERE type=1;
UPDATE table2 SET summary=@A WHERE type=1;
COMMIT;