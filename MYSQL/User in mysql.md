CREATE USER 'Linus'@'%' IDENTIFIED BY 'keinpasswort'
GRANT UPDATE, SELECT on bank.* TO 'linus'@'%';