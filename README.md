# clickhouse-cluster

Кластер из 3-х нод zookeeper и 4-х нод clickhouse (2 шарда по 2 реплики)

# Запустить zookeeper
```
ansible-playbook site_zk.yml
```

# Запустить clickhouse
```
ansible-playbook site_ch.yml
```

# Создать реплицированную таблицу
```
CREATE TABLE transaction_logs_shard ON CLUSTER 'cluster_1'
(
 transaction_id Int64,
 client_id  Int64,
 timestamp  DateTime
)
Engine=ReplicatedMergeTree('/clickhouse/tables/{shard}/transaction_logs_shard', '{replica}')
PARTITION BY client_id
ORDER BY timestamp;
```

# Создать распределенную таблицу
```
CREATE TABLE transaction_logs  ON CLUSTER 'cluster_1'
(
 transaction_id Int64,
 client_id  Int64,
 timestamp  DateTime
)
ENGINE = Distributed(cluster_1, default,transaction_logs_shard, (client_id) );
```

# Загрузить тестовые данные
```
clickhouse-client  --format_csv_delimiter="," --query "INSERT INTO transaction_logs FORMAT CSVWithNames" < dataset.csv
```
