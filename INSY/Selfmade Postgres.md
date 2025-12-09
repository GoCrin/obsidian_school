```Dockerfile
FROM alpine:latest

RUN apk update && \
    apk add --no-cache postgresql postgresql-contrib su-exec && \
    mkdir -p /var/lib/postgresql/data /run/postgresql && \
    chown -R postgres:postgres /var/lib/postgresql /run/postgresql

ENV PGDATA=/var/lib/postgresql/data
COPY init-postgres.sh /init-postgres.sh
USER postgres

RUN initdb -D "$PGDATA"

EXPOSE 5432

CMD ["/init-postgres.sh"]
```

```sh
#!/bin/sh
set -e

postgres -D "$PGDATA" &
pid=$!

until pg_isready; do
  sleep 1
done

psql -U postgres <<EOF
CREATE DATABASE mydatabase;
EOF

wait $pid
```


```Bash
sudo docker run -d --network host --name run-selfmade-postgres selfmade-postgres
```

Als Nutzer `postgres` auf Postgresql zugreifen
```Bash
psql -h localhost -p 5432
```
