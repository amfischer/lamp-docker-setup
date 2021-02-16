# lamp-docker-setup

- https://github.com/sprintcube/docker-compose-lamp

### xdebug
- https://github.com/docker/for-win/issues/9306
- https://stackoverflow.com/questions/49677199/how-do-i-get-xdebug-step-debugging-working-with-ddev

### permissions
 - https://vsupalov.com/docker-shared-permissions/

### tar files
 - https://wiki.haskell.org/How_to_unpack_a_tar_file_in_Windows

### seeding db from zipped tar
 - `make dbcreate`
 - `docker-compose exec db bash`
 - `cd /seed && gzip -d report.sql.gz`
 - `mysql -uroot -p app < report.sql`