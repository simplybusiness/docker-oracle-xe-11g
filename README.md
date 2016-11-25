docker-oracle-xe-11g
============================
(forked from [wnameless/docker-oracle-xe-11g](https://github.com/wnameless/docker-oracle-xe-11g))

Oracle Express Edition 11g Release 2 on Ubuntu 16.04 LTS

This **Dockerfile** is a [trusted build](https://registry.hub.docker.com/u/simplybusiness/oracle-xe-11g/) of [Docker Registry](https://registry.hub.docker.com/).

### Installation(with Ubuntu 16.04)
```
docker pull simplybusiness/oracle-xe-11g
```
### Building image locally
```
git clone git@github.com:simplybusiness/docker-oracle-xe-11g.git
cd docker-oracle-xe-11g
docker build -t simplybusiness/oracle-xe-11g:local .
```

### Running
Run with 22, 1521, 8080 ports opened:
```
docker run -d -p 49160:22 -p 49161:1521 -p 49162:8080 simplybusiness/oracle-xe-11g
```

Run this, if you want the database to be connected remotely:
```
docker run -d -p 49160:22 -p 49161:1521 -e ORACLE_ALLOW_REMOTE=true simplybusiness/oracle-xe-11g
```

Connect database with following setting:
```
hostname: localhost
port: 49161
sid: xe
username: system
password: oracle
```

Password for SYS & SYSTEM
```
oracle
```

Login by SSH
```
ssh root@localhost -p 49160
password: admin
```

Support custom DB Initialization
```
# Dockerfile
FROM simplybusiness/oracle-xe-11g

ADD init.sql /docker-entrypoint-initdb.d/
```
