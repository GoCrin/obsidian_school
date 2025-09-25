Webservices bieten die Möglichkeit Dienste, die ein Server zur Verfügung stellt anzusprechen. Restful Webservices folgen den REST Grundprinzipien. Zu diesen zählen: <u>Eindeutige Identifikation von Ressourcen:</u> z.B. `https://shop.htlhl.at/products/75`
<u>Verwendung von http-Standardmethoden:</u> z.B. `GET`, `POST`, `PUT`, `PATCH`, `DELETE`

## Analogie objektorientierte Methode vs. Restful Webservice:

| OOP. Methode                    | Restful Webservice | URL Beispiel                       |
| ------------------------------- | ------------------ | ---------------------------------- |
| `getUsers()`                    | `GET`              | `https://shop.htlhl.at/users`      |
| `updateUser(int id, User user)` | `PATCH`            | `https://shop.htlhl.at/users/{id}` |
| `updateUser(User user)`         | `POST`             | `https://shop.htlhl.at/users`      |
| `updateUser(int id)`            | `DELETE`           | `https://shop.htlhl.at/users/{id}` |
