## Django Connection Pooling
===============================================

1. Django **do not implement connection pooling** at core. Because:
    - Third party apps as pgbouncer do it better ([Answer](https://stackoverflow.com/questions/4546059/why-doesnt-django-support-connection-pool))
    
    For detail, Go through group discussion, [here](https://groups.google.com/g/django-developers/c/NwY9CHM4xpU)

2. Persistent connection eliminates overhead of creating connection.

3. When django's transacton middleware is enabled, each request is wrapped in a single transaction, which reserves a connection.

4. There are database library for django which implements SQLAlchemy pool to implement Connection pooling in django.
    - [django-postgrespool](https://github.com/heroku-python/django-postgrespool/)
    - [django-db-connection-pool](https://github.com/altairbow/django-db-connection-pool/)
    
5. For small-medium application persistent connection is good.

6. For large scale application persistent connection exponentially increases cost and resources.

7. Set low value for **CONN_MAX_AGE** in django admin to prevent maximum connection to db server.
