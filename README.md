# infra-notes
This repo is made to have some useful notes to maintain a VPS

** Install docker through shell script
```wget -nv -O - https://get.docker.com/ | sh```

** Backup all databases from a database container which the name contains db

```docker exec $(docker ps --filter name=db -q) sh -c \ 'mysqldump --all-databases --quick --single-transaction --skip-lock-tables --flush-privileges -uroot -p"$MYSQL_ROOT_PASSWORD"' \ | gzip > ./backup.sql.gz```

** Restore docker database

```gunzip -k ./backup.sql.gz
cat backup.sql | docker exec -i db sh -c 'mysql -uroot -p"$MYSQL_ROOT_PASSWORD"'```
