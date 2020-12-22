# infra-notes
This repo is made to have some useful notes to maintain a VPS


# Backup all databases from a database container which the name contains db 
docker exec $(docker ps --filter name=db -q) sh -c \ 'mysqldump --all-databases --quick --single-transaction --skip-lock-tables --flush-privileges -uroot -p"$MYSQL_ROOT_PASSWORD"' \ | gzip > ./backup.sql.gz
