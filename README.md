# PostgreSQL 10 for docker

## 需求環境

1. docker
2. docker-compose

## 使用說明

### 修改啟動設定檔參數

```bash
cp docker-compose.yml.example docker-compose.yml
```

docker-compose.yml

```
POSTGRES_USER: 使用者名稱
POSTGRES_PASSWORD: 使用者密碼
POSTGRES_DB: 資料庫名稱
```

### 啟動`PostgreSQL`

```bash
docker-compose up
```

### 背景啟動`PostgreSQL`

```bash
docker-compose up -d
```

### 結束`PostgreSQL`

```bash
docker-compose down
```

### 一些常用的操作指令

1. 查看目前有運行的`docker container`

```bash
docker ps
```

2. 連線到某個`docker container`

```bash
docker exec -it CONTAINER_ID bash
```

--- 以下指令請連線到`docker container`中執行 ---

3. 從檔案匯入資料庫

```bash
psql 資料庫名稱 使用者名稱 -f 檔名.sql
```

4. 匯出資料庫到檔案

```bash
pg_dump 資料庫名稱 -U 使用者名稱 -f 檔名.sql
```

5. 與資料庫連線

```bash
psql 資料庫名稱 使用者名稱
```

--- 以下指令請連線到資料庫中執行 ---

6. 列出所有資料表

```
\dt
```

7. 列出資料表所有欄位名稱

```
\d 資料表名稱
```

8. 檢索資料表所有內容

```
select * from 資料表名稱;
```

### 清空`PostgreSQL`資料庫

清除資料有兩種方式

1. 在結束`PostgreSQL`同時清除資料

```bash
docker-compose down -v
```

2. 清除`docker volume`，本專案`VOLUME_NAME`是`postgresql_docker_pgdata`

```
docker volume ls
docker volume rm postgresql_docker_pgdata
```
