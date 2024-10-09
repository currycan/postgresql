## 修改hosts文件

[containers/bitnami/pgpool/README.md at main · bitnami/containers](https://github.com/bitnami/containers/blob/main/bitnami/pgpool/README.md)
[Docker启动PostgreSQL时创建多个数据库# 1 前言 在文章《\[Docker启动PostgreSQL并推荐几 - 掘金](https://juejin.cn/post/6976281873907449893)

```bash

hostnamectl set-hostname pg-0
hostnamectl set-hostname pg-1

hostnamectl set-hostname pgpool
```

## 创建目录

```bash
psql -h 192.168.88.88 -U $POSTGRES_USER

psql -h 192.168.88.88 -U dbtest

```

```bash
docker volume ls

chmod 775 sql/db-initializer.sh

docker compose down
docker volume rm pg_pg_0_data pg_pg_1_data pg_pgadmin
docker volume rm -f normal_pgadmin normal_postgres
docker compose up -d
docker compose logs -f pg-0
```

```sql
CREATE DATABASE keycloak;
CREATE USER keycloak_owner with encrypted password 'keycloak123';
GRANT ALL PRIVILEGES ON DATABASE keycloak TO keycloak_owner ;

\connect keycloak;
GRANT ALL ON SCHEMA public TO keycloak_owner;
```


## pgpool 需要生成 pool_passwd

对应需要设置环境变量：PGPOOL_POSTGRES_CUSTOM_USERS和PGPOOL_POSTGRES_CUSTOM_PASSWORDS，多用户之间以分号隔开
