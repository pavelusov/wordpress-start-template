# A Wordpress template with a manual setup


## Start setup
`
docker-compose up -d
`

## Creating database dumps
`docker exec db sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > ./db_dump/all-databases.sql`
`docker exec db sh -c 'exec mysqldump wordpress -uroot -p"$MYSQL_ROOT_PASSWORD"' > ./db_dump/wordpress.sql`

## Restoring data from dump files
`docker exec -i db sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < ./db_dump/all-databases.sql`
