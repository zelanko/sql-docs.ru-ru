---
title: "Объекты T-SQL PolyBase | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-polybase"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolyBase, основные понятия"
  - "PolyBase, инструкции SQL"
  - "PolyBase, объекты SQL"
ms.assetid: ef5d6c40-6ce6-4cf0-8ad3-38f98b32f98e
caps.latest.revision: 20
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 18
---
# Объекты T-SQL PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы использовать PolyBase, необходимо создать внешние таблицы для ссылок на внешние данные.  
  
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)  
  
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)  
  
## Предварительные требования  
 Настройте PolyBase. См. раздел [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).  
  
## Создание внешних таблиц для Hadoop  
 **1. Создайте учетные данные области базы данных.**  
  
 Этот шаг является обязательным только для кластеров Hadoop, защищенных с помощью Kerberos.  
  
```sql  
-- Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Kerberos-secured Hadoop clusters.  
-- IDENTITY: the Kerberos user name.  
-- SECRET: the Kerberos password  
  
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1   
WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
  
```  
  
 **2. Создайте внешний источник данных.**  
  
```sql  
-- Create an external data source.  
-- LOCATION (Required) : Hadoop Name Node IP address and port.  
-- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
-- CREDENTIAL (Optional):  the database scoped credential, created above.  
  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
        TYPE = HADOOP,   
        LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',   
        RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',   
        CREDENTIAL = HadoopUser1      
);  
  
```  
  
 **3. Создайте формат внешнего файла.**  
  
```sql  
-- Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
```  
  
 **4. Создайте внешнюю таблицу.**  
  
```sql  
-- Create an external table pointing to data stored in Hadoop.  
-- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = MyHadoopCluster,  
        FILE_FORMAT = TextFileFormat  
);  
  
```  
  
 **5. Создание статистики**  
  
```sql  
-- Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## Создание внешней таблицы для хранилища BLOB-объектов Azure  
 **1. Создайте учетные данные области базы данных.**  
  
```sql  
-- Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Azure blob storage.  
-- IDENTITY: any string (this is not used for authentication to Azure storage).  
-- SECRET: your Azure storage account key.  
  
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential   
WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';  
  
```  
  
 **2. Создайте внешний источник данных.**  
  
```sql  
-- Create an external data source.  
-- LOCATION:  Azure account storage account name and blob container name.  
-- CREDENTIAL: The database scoped credential created above.  
  
CREATE EXTERNAL DATA SOURCE AzureStorage with (  
        TYPE = HADOOP,   
        LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
        CREDENTIAL = AzureStorageCredential  
);  
  
```  
  
 **3. Создайте формат внешнего файла.**  
  
```sql  
-- Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
```  
  
 **4. Создайте внешнюю таблицу.**  
  
```sql  
-- Create an external table pointing to data stored in Azure storage.  
-- LOCATION: path to a file or directory that contains the data (relative to the blob container).  
-- To point to all files under the blob container, use LOCATION='/'   
  
CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
        [SensorKey] int NOT NULL,   
        [CustomerKey] int NOT NULL,   
        [GeographyKey] int NULL,   
        [Speed] float NOT NULL,   
        [YearMeasured] int NOT NULL  
)  
WITH (LOCATION='/Demo/',   
        DATA_SOURCE = AzureStorage,  
        FILE_FORMAT = TextFileFormat  
);  
  
```  
  
 **5. Создание статистики**  
  
```sql  
-- Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## Следующие шаги  
 Примеры запросов см. в разделе [Запросы PolyBase](../../relational-databases/polybase/polybase-queries.md).  
  
## См. также:  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  