# PHP Docker Setup

> Note this setup uses the MySQL for ARM processors, for changes for Intel see below

To build

```bash
$ docker compose build
```

To run container

```bash
$ docker compose up
```

To stop container

```bash
$ docker compose down
```

To access command prompt, from another window


```bash
$ docker compose exec app bash
```


## Mysql

You can access the database server from within the docker container using the host `mysql` from outside the container, you use the host `127.0.0.1`.

E.g. DSN `DB_DSN=mysql:host=mysql;port=3306;dbname=your_app`

If you are working on an Intel processor, then change the `mysql` section in the `docker-compose.yml`, i think this should work.

```
mysql
    image: mysql:8.0
    volumes:
        - mysql-data:/var/lib/mysql
    environment:
        MYSQL_ROOT_PASSWORD: root
    ports:
        - "3306:3306"
    command: --default-authentication-plugin=mysql_native_password
```