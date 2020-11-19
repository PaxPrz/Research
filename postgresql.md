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

### Monitoring and Statistic collection

- From official [documentation](https://www.postgresql.org/docs/13/monitoring.html)

`ps auxww | grep ^postgres` shows current connections also

1. Monitoring stats can be disabled too from configuration file.

2. Presently, the collector can count accesses to tables and indexes in both disk-block and individual-row terms

3. From configuration file:
    - The parameter **track_activities** enables monitoring of the current command being executed by any server process.
    - The parameter **track_counts** controls whether statistics are collected about table and index accesses.
    - The parameter **track_functions** enables tracking of usage of user-defined functions.
    - The parameter **track_io_timing** enables monitoring of block read and write times.
    - **stats_temp_directory** : The statistics collector transmits the collected information to other PostgreSQL processes through temporary files

4. Get Active connection
    - `SELECT sum(numbackends) FROM pg_stat_database;` 
    
5. Monitoring from pgadmin4:
    - ```
        /*pga4dash*/
        SELECT 'session_stats' AS chart_name, row_to_json(t) AS chart_data  
        FROM (SELECT 
          (SELECT count(*) FROM pg_stat_activity WHERE datname = (SELECT datname FROM pg_database WHERE oid = 16384)) AS "Total",
          (SELECT count(*) FROM pg_stat_activity WHERE state = 'active' AND datname = (SELECT datname FROM pg_database WHERE oid = 16384))  AS "Active", 
          (SELECT count(*) FROM pg_stat_activity WHERE state = 'idle' AND datname = (SELECT datname FROM pg_database WHERE oid = 16384))  AS "Idle"
        ) t
        UNION ALL
        SELECT 'tps_stats' AS chart_name, row_to_json(t) AS chart_data 
        FROM (SELECT 
          (SELECT sum(xact_commit) + sum(xact_rollback) FROM pg_stat_database WHERE datname = (SELECT datname FROM pg_database WHERE oid = 16384)) AS "Transactions",
          (SELECT sum(xact_commit) FROM pg_stat_database WHERE datname = (SELECT datname FROM pg_database WHERE oid = 16384)) AS "Commits",
          (SELECT sum(xact_rollback) FROM pg_stat_database WHERE datname = (SELECT datname FROM pg_database WHERE oid = 16384)) AS "Rollbacks"
       ) t;
       ```
