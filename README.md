# catalog-service

Service created as project in book Cloud Native Spring in Action by Thomas Vitale

### To create the docker network

```
docker network create catalog-network
```

### To run Postgres

Note: Create a directory named <b><i>postgres-data</i></b> for local persistent storage

```
docker run -d --name polar-postgres --net catalog-network \
-e POSTGRES_USER=user -e POSTGRES_PASSWORD=password -e POSTGRES_DB=polardb_catalog \
-p 5432:5432 -v ./postgres-data:/var/lib/postgresql/data postgres:14.4
```

### To build jar

```
./gradlew clean bootJar
```

### To build image

```
docker build -t catalog-service .
```

### To run the image

```
docker run -d \
--name catalog-service \
--net catalog-network \
-p 9001:9001 \
-e SPRING_DATASOURCE_URL=jdbc:postgresql://polar-postgres:5432/polardb_catalog \
-e SPRING_PROFILES_ACTIVE=testdata \
catalog-service
```