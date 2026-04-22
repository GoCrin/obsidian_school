# Wordpress

```bash
sudo docker run --name insy-mysql --network host -e MYSQL_ROOT_PASSWORD=root -d mysql
```

```bash
sudo docker run --name insy-wp -e WORDPRESS_DB_HOST=127.0.0.1:3306 -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=root -e WORDPRESS_DB_NAME=wordpress --network host wordpress
```

```bash
mariadb -h 127.0.0.1 -P 3306 -u root -proot
```

