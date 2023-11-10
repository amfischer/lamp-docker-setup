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
 - Unzip first
   - `cd /seed && gzip -d report.sql.gz`
   - `mysql -uroot -p app < report.sql`
 - One-liner
   - `zcat report.sql.gz | mysql -uroot -p app`

### mysqldump and create zipped file
- [commands reference](https://fixyacloud.wordpress.com/2020/01/26/mysqldump-to-a-tar-gz/)
- `scp <user>@<ip-address>:/home/forge/mz.sql.gz /home/aaron/projects/mz.sql.gz`


### latest wordpress
 - `curl -O https://wordpress.org/latest.tar.gz`
 - `tar xzvf <.tar.gz file>`
 - [docker compose setup with wordpress image](https://mklasen.com/adding-and-using-wp-cli-in-a-docker-compose-setup/)
