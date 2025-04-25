https://symfony.com/doc/current/mercure.html#running-a-mercure-hub

Um Mercure auf dem Symfony local Server zu ver wenden muss dieser nun mit der option `--no-tls` gestartet werden (keine Ahnung was `-d` macht)

```
symfony server:start --no-tls -d
```

# Installation

```
composer require mercure
```

