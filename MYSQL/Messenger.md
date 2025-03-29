### User
* username
* password
* profilepicture
### Channel
* member
* messages
### Message
* author
* content
* time it was sent

### Beziehungen
1-N User : N Channel
1 User : N Message
1 Channel : N Message

mindestens ein Nutzer hat beliebig viele Channel
Ein Nutzer hat beliebig viele Nachrichten
Ein Channel hat beliebig viele Nachrichten

### Design choices

* Channels haben keinen Admin. Werden bei verlassen der letzten Person gelöscht