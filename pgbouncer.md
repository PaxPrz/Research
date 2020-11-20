# PgBouncer

Lightweight connection pooler for PostgreSQL

### Installation:

From official [documentation](https://www.pgbouncer.org/install.html)

### Configuration:

> /etc/pgbouncer/pgbouncer.ini

```
[databases]
cdr = host=127.0.0.1 port=5432 dbname=cdr

[pgbouncer]
listen_addr = 127.0.0.1
listen_port = 6432
auth_type = md5
auth_file = /etc/pgbouncer/userlist.txt
pool_mode = transaction
max_client_conn = 100
default_pool_size = 10
min_pool_size = 5
reserve_pool_size = 10
reserve_pool_timeout = 5
max_db_connections = 20
max_user_connections = 10
ignore_startup_parameters = extra_float_digits

# Log settings
admin_users = postgres

# Connection sanity checks, timeouts
server_reset_query = DISCARD ALL
server_idle_timeout = 10
```

> /etc/pgbouncer/userlist.txt

```
"username" "password"
....
```

### Starting service

`sudo service pgbouncer start`

Connecting through PgBouncer is same as the way you connect to postgres with psql

`psql -h 127.0.0.1 -p 6432 -U username pgbouncer`

### Monitoring

`> show stats;`

- Displays 
``` database  | total_xact_count | total_query_count | total_received | total_sent | total_xact_time | total_query_time | total_wait_time | avg_xact_count | avg_query_count | avg_recv | avg_sent | avg_xact_time | avg_query_time | avg_wait_time```

`> show pools;`

- Displays ``` database  |   user    | cl_active | cl_waiting | sv_active | sv_idle | sv_used | sv_tested | sv_login | maxwait | maxwait_us | pool_mode ```

More queries are available. [Here](https://www.pgbouncer.org/usage.html) is the detail of each query.


## Best Resources to learn:

1. From [heroku](https://devcenter.heroku.com/articles/best-practices-pgbouncer-configuration) about pgbouncer modes and work
