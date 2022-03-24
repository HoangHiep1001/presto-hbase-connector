## --------TRINO HBASE CONNECTOR---------

# Note: only support query primitive data types

# 1. Build

````mvn clean package````

# 2. Copy jar file to folder plugin

````copy jar file from target to plugin````

# 3. Define schema for hbase table

- Example:

````
   {
   "tableName": "tableName",
   "schemaName": "default",
   "rowKeyFormat": "userId,contactId",
   "rowKeySeparator": "-",
   "rowKeyFirstCharRange": "a~z,0~9",
   "columns": [{
   "family": "",
   "columnName": "rowkey",
   "type": "varchar",
   "isRowKey": true
   }, {
   "family": "f",
   "columnName": "userId",
   "comment": "Column for test!",
   "type": "bigint",
   "isRowKey": false
   }, {
   "family": "f",
   "columnName": "contactId",
   "type": "bigint",
   "isRowKey": false
   }]
   }
   ````

#3. Create properties file hbase connect

- Example:

````
  connector.name=hbase
  zookeeper-quorum=host:2181
  zookeeper-client-port=2181
  zookeeper-znode-parent=/hbase
  hbase-cluster-distributed=true
  random-schedule-redundant-split=false
  meta-dir=/data1/trino-test/trino-server/etc/hbase
````

# 4. Restart trino