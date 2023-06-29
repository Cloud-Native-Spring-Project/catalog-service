# catalog-service

Service created as project in book Cloud Native Spring in Action by Thomas Vitale

### To run Postgres

Note: Create a directory named <b><i>postgres-data</i></b> for local persistent storage

```
docker run -d \
    --name polar-postgres \
    -e POSTGRES_USER=user \
    -e POSTGRES_PASSWORD=password \
    -e POSTGRES_DB=polardb_catalog \
    -p 5432:5432 \
    -v ./postgres-data:/var/lib/postgresql/data
    postgres:14.4
```