## Postgresql

### Download and Installation guide:

Can be found easily in google. Some helpful resources will be: 

- Postgresql official [site](https://www.postgresql.org)

### Documentation

- Postgresql official [documentation](https://www.postgresql.org/docs/13/index.html) for version 13.

### Configuration

`/etc/postgresql/${POSTGRES_VERSION}/main/postgresql.conf`

Start only specific version of postgresql

`sudo service postgresql@${POSTGRES_VERSION}-main start`

### Dump and restore

Take a dump

`$ pg_dump -U username db > file.sql`

`$ pg_dumpall > all.sql`

Do a restore

`$ psql -U username db < file.sql`

### Monitoring

- From official [documentation](https://www.postgresql.org/docs/13/monitoring.html)

`ps auxww | grep ^postgres` shows current connections also

1. Monitoring stats can be disabled too from configuration file.
