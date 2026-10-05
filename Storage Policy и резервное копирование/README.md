Развернут Minio:

![1791221886708](images/README/1791221886708.png)

docker-compose.yaml:

```
services:
  minio:
    image: pgsty/minio:latest
    container_name: minio-staging
    restart: unless-stopped
    environment:
      - MINIO_ROOT_USER=${MINIO_ROOT_USER:-minio}
      - MINIO_ROOT_PASSWORD=${MINIO_ROOT_PASSWORD:-miniominio}
    command: server /data --console-address ":19010" --address ":19009"
    volumes:
      - minio-data:/data
    network_mode: host
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:19009/minio/health/live"]
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 30s

volumes:
  minio-data:
```

Создание бэкапа:

```
clickhouse-backup create_remote test
```

![1791221967905](images/README/1791221967905.png)

Исходные таблицы:

![1791222012403](images/README/1791222012403.png)

Удаляю две таблицы:

![1791222038072](images/README/1791222038072.png)

Выполнение команды по восстановлению:

```
clickhouse-backup restore_remote test
```

Восстановленные таблицы:

![1791222544376](images/README/1791222544376.png)
