---
title: "СОЗДАЙТЕ внешний ИСТОЧНИК данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL DATA SOURCE
- CREATE_EXTERNAL_DATA_SOURCE
dev_langs: TSQL
helpviewer_keywords:
- External
- External, data source
- PolyBase, create data source
ms.assetid: 75d8a220-0f4d-4d91-8ba4-9d852b945509
caps.latest.revision: "58"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8e5f0a03ef6efa09218cc6740df4439a25eb7265
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-external-data-source-transact-sql"></a>СОЗДАЙТЕ внешний ИСТОЧНИК данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Создает внешний источник данных для PolyBase, запросы эластичной базы данных или хранилища BLOB-объектов Azure. В зависимости от сценария синтаксис существенно отличается. Источник данных, созданный для PolyBase не может использоваться для запросов эластичной базы данных.  Аналогичным образом источник данных, созданный для запросов эластичной базы данных не может использоваться для PolyBase и т. д. 
  
> [!NOTE]  
>  PolyBase поддерживается только в SQL Server 2016, хранилище данных SQL Azure и параллельных хранилищ данных. Эластичный запросы к базе данных поддерживаются только в базе данных SQL Azure v12 или более поздней версии.  
  
 Для сценариев PolyBase с внешним источником данных является System файла Hadoop (HDFS), контейнер больших двоичных объектов хранилища Azure или хранилища Озера данных Azure. Дополнительные сведения см. в разделе [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 Для сценариев с запросами эластичной базы данных внешнего источника является диспетчера карты сегментов (в базе данных SQL Azure) или удаленной базы данных (в базе данных SQL Azure).  Используйте [sp_execute_remote &#40; База данных Azure SQL &#41; ](../../relational-databases/system-stored-procedures/sp-execute-remote-azure-sql-database.md) после создания внешнего источника данных. Дополнительные сведения см. в разделе [запроса эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  

  Источник данных внешнего хранилища BLOB-объектов Azure поддерживает `BULK INSERT` и `OPENROWSET` синтаксис и отличается от хранения больших двоичных объектов Azure для PolyBase.
    
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- PolyBase only:  Hadoop cluster as data source   
-- (on SQL Server 2016)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,
        LOCATION = 'hdfs://NameNode_URI[:port]'  
        [, RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI[:port]' ]  
        [, CREDENTIAL = credential_name ]
    )
[;]  
  
-- PolyBase only: Azure Storage Blob as data source   
-- (on SQL Server 2016 and Azure SQL Data Warehouse)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = HADOOP,  
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
[;]

-- PolyBase only: Azure Data Lake Store
-- (on Azure SQL Data Warehouse)
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (
    TYPE = HADOOP,
    LOCATION = 'adl://<AzureDataLake account_name>.azuredatalake.net',
    CREDENTIAL = AzureStorageCredential
);

-- PolyBase only: Hadoop cluster as data source
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP, 
        LOCATION = 'hdfs://NameNode_URI[:port]'
        [, JOB_TRACKER_LOCATION = 'JobTracker_URI[:port]' ]
    )
[;]

-- PolyBase only: Azure Storage Blob as data source 
-- (on Parallel Data Warehouse)
CREATE EXTERNAL DATA SOURCE data_source_name
    WITH ( 
        TYPE = HADOOP,
        LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'
    )
[;]
  
-- Elastic Database query only: a shard map manager as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = SHARD_MAP_MANAGER,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '\<ElasticDatabase_ShardMapManagerDb'>,  
        CREDENTIAL = <ElasticDBQueryCred>,  
        SHARD_MAP_NAME = '<ShardMapName>'  
    )  
[;]  
  
-- Elastic Database query only: a remote database on Azure SQL Database as data source   
-- (only on Azure SQL Database)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = RDBMS,  
        LOCATION = '<server_name>.database.windows.net',  
        DATABASE_NAME = '<Remote_Database_Name>',  
        CREDENTIAL = <SQL_Credential>  
    )  
[;]  

-- Bulk operations only: Azure Storage Blob as data source   
-- (on SQL Server 2017 or later, and Azure SQL Database).
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'https://storage_account_name.blob.core.windows.net/container_name'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_источника_данных* задает пользовательское имя для источника данных. Имя должно быть уникальным в пределах базы данных в SQL Server, базы данных SQL Azure и хранилище данных SQL Azure. Имя должно быть уникальным в пределах сервера в Parallel Data Warehouse.
  
 ТИП = [HADOOP | SHARD_MAP_MANAGER | RDBMS | BLOB_STORAGE]  
 Указывает тип источника данных. Используйте HADOOP, если внешний источник данных Hadoop или BLOB-хранилища Azure для Hadoop. Используете SHARD_MAP_MANAGER при создании внешнего источника данных для запроса эластичной базы данных для сегментирования в базе данных SQL Azure. Используйте реляционной СУБД с внешними источниками данных для запросов между базами данных с запросом эластичной базы данных в базе данных SQL Azure.  Использовать BLOB_STORAGE при выполнении массовых операций с помощью [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) или [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
  
РАСПОЛОЖЕНИЕ = \<location_path > **HADOOP**    
Для HADOOP указывает универсального ресурса (URI) для кластера Hadoop.  
`LOCATION = 'hdfs:\/\/*NameNode\_URI*\[:*port*\]'`  
NameNode_URI: Имя компьютера или IP-адрес кластера Hadoop Namenode.  
порт: Namenode IPC-порт. Это указывается в параметре конфигурации fs.default.name Hadoop. Если значение не указано, по умолчанию будет использоваться 8020.  
Пример: `LOCATION = 'hdfs://10.10.10.10:8020'`

Для хранения больших двоичных объектов Azure с Hadoop указывает URI для подключения к хранилищу больших двоичных объектов.  
`LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'`  
wasb [s]: Указывает протокол для хранилища BLOB-объектов Azure. [S] является необязательным и указывает безопасное соединение SSL. данные, отправляемые из SQL Server надежно шифруются по протоколу SSL. Настоятельно рекомендуется использовать «wasbs» вместо «wasb». Обратите внимание, что расположение может использовать asv [s] вместо wasb [s]. Синтаксис asv [s] является устаревшей и будет удален в будущем выпуске.  
контейнер: задает имя контейнера хранилища BLOB-объектов Azure. Чтобы указать корневой контейнер домена учетной записи хранения, используйте имя домена вместо имени контейнера. Контейнеры корневой являются только для чтения, поэтому данные не записываются в контейнер.  
account_name: полное доменное имя (FQDN) учетной записи хранилища Azure.  
Пример: `LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'`

Для хранилища Озера данных Azure местоположение указывает URI для подключения к хранилищу Озера данных Azure.



**SHARD_MAP_MANAGER**   
 Для SHARD_MAP_MANAGER указывает имя логического сервера, на котором размещена диспетчера карты сегментов в базе данных SQL Azure или базы данных SQL Server на виртуальной машине Azure.
 
 ```
 CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH
  (TYPE = SHARD_MAP_MANAGER,
  LOCATION = '<server_name>.database.windows.net',
  DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
  CREDENTIAL = ElasticDBQueryCred,
  SHARD_MAP_NAME = 'CustomerIDShardMap'
) ;
```

Пошаговое руководство см. в разделе [Приступая к работе с эластичной запросов для сегментирования (горизонтальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/).
  
**RDBMS**   
Для реляционной СУБД указывает имя логического сервера удаленной базы данных в базе данных SQL Azure.  

```  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';  
  
CREATE DATABASE SCOPED CREDENTIAL SQL_Credential    
WITH IDENTITY = '<username>',  
SECRET = '<password>';  
  
CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc WITH   
    (TYPE = RDBMS,   
    LOCATION = '<server_name>.database.windows.net',   
    DATABASE_NAME = 'Customers',   
    CREDENTIAL = SQL_Credential   
) ;   
```  
  
Пошаговое руководство по реляционной СУБД, в разделе [Приступая к работе с межбазовые запросы (вертикальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/).  

**BLOB_STORAGE**   
Для массовых операций, `LOCATION` должен быть допустимым URL-адрес хранилища больших двоичных объектов Azure и контейнер. Не размещайте  **/** , имя файла или общие параметры подписи доступа в конце `LOCATION` URL-адрес.   
Учетные данные, используемые, должен быть создан с помощью `SHARED ACCESS SIGNATURE` с удостоверением. Дополнительные сведения о подписанных URL-адресах см. в [этой статье](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1). Пример доступа к хранилищу BLOB-объектов, см. пример F [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md). 

  
 RESOURCE_MANAGER_LOCATION = "*ResourceManager_URI*[:*порт*]"  
 Указывает расположение диспетчера ресурсов Hadoop. Если указано, оптимизатор запросов может принять решение на основе стоимости для предварительной обработки данных для запроса PolyBase при помощи возможностей вычислений в Hadoop и MapReduce. Вызывается Включение предиката, это может значительно сократить объем данных, передаваемых между Hadoop и SQL и таким образом повысить производительность запросов.  
  
 Если этот параметр не указан, принудительной отправки вычислений в Hadoop отключена для обработки запросов PolyBase.  
 
Если порт не указан, значение по умолчанию определяется с помощью параметра текущей конфигурации 'hadoop connectivity'.

|Подключения к Hadoop.|Порт по умолчанию диспетчер ресурсов|
|-------------------|-----------------------------|
|1|50300|
|2|50300|
|3|8021|
|4|8032|
|5|8050|
|6|8032|
|7|8050|

Полный список типа распределений и поддерживает подключения к каждому значению типа версии, в разделе [конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).
  
> [!IMPORTANT]  
>  Значение RESOURCE_MANAGER_LOCATION является строкой и не проверяется при создании внешнего источника данных. При вводе неверного значения может привести к задержкам будущих, при доступе к расположению.  
  
 Примеры Hadoop.  
  
-   Hortonworks HDP 2.0, 2.1, 2.2. 2.3 в Windows:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
-   Hortonworks HDP 1.3 в Windows:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Hortonworks HDP 2.0, 2.1, 2.2 и 2.3 в Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8050'  
    ```  
  
-   Hortonworks HDP 1.3 в Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Cloudera 4.3 в Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8021'  
    ```  
  
-   Cloudera 5.1 5.11 в Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
 Учетные данные = *credential_name*  
 Указывает учетные данные уровня базы данных для проверки подлинности на внешнем источнике данных. Пример см. в разделе [. Создание источника внешних данных хранилища больших двоичных объектов Azure](../../t-sql/statements/create-external-data-source-transact-sql.md#credential). Создание учетных данных, в разделе [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md). Обратите внимание, что учетные данные не требуется для общих наборов данных, которые разрешить анонимный доступ. 
  
 DATABASE_NAME = *'QueryDatabaseName'*  
 Имя базы данных, которое работает в качестве диспетчера карты сегментов (для SHARD_MAP_MANAGER) или удаленной базы данных (для реляционной СУБД).  
  
 SHARD_MAP_NAME = *«ShardMapName»*  
 Для SHARD_MAP_MANAGER. Имя карты сегментов. Дополнительные сведения о создании карты сегментов см. в разделе [Приступая к работе с запросом эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)  
  
## <a name="polybase-specific-notes"></a>Заметки о конкретных PolyBase  
Полный список поддерживаемых внешних источников данных см. в разделе [конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

 Чтобы использовать PolyBase, необходимые для создания этих трех объектов.  
  
-   Внешний источник данных.  
  
-   Формат внешнего файла и  
  
-   Внешнюю таблицу, которая ссылается на внешний источник данных и формата внешнего файла.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL на базу данных в хранилища данных SQL, SQL Server, APS 2016 и баз данных SQL Server.

> [!IMPORTANT]  
>  В предыдущих выпусках PDW создайте разрешения ALTER ANY EXTERNAL DATA SOURCE источника внешних данных.
  
  
## <a name="error-handling"></a>Обработка ошибок  
 Ошибка выполнения происходит, если внешние источники данных Hadoop не согласованы о необходимости RESOURCE_MANAGER_LOCATION определен. Таким образом невозможно определить два внешних источников данных, ссылающиеся на том же кластере Hadoop, а затем предоставлять расположение диспетчера ресурсов для одного, а не для другого.  
  
 Ядро SQL не выполняется проверка существования внешнего источника данных при создании объекта источника внешних данных. Если источник данных не существует во время выполнения запроса завершится ошибкой.  
  
## <a name="general-remarks"></a>Общие замечания  
Для PolyBase внешний источник данных области базы данных в SQL Server и хранилище данных SQL. Это уровня сервера в параллельное хранилище данных.
  
Для PolyBase Если определен RESOURCE_MANAGER_LOCATION или JOB_TRACKER_LOCATION, оптимизатор запросов будет рассматривать оптимизации каждого запроса, запуская карты уменьшить задание на внешнего источника Hadoop и передают вычисления. Это полностью принятия решений, основанный на стоимости.  

Чтобы обеспечить успешных запросов PolyBase в случае отработки отказа Hadoop NameNode, рассмотрите возможность использования виртуального IP-адреса для NameNode кластера Hadoop. Если не используется виртуальный IP-адрес для Hadoop NameNode, при отработке отказа Hadoop NameNode имеется объект ALTER EXTERNAL DATA SOURCE, чтобы он указывал на новое место.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Все источники данных, определенные в том же расположении кластера Hadoop необходимо использовать тот же параметр для RESOURCE_MANAGER_LOCATION или JOB_TRACKER_LOCATION. Если существует несоответствие, возникнет ошибка времени выполнения.  
  
 Если настройка кластера Hadoop с именем и к внешнему источнику данных использует IP-адрес для кластера расположения, PolyBase должен иметь возможность разрешения имени кластера при использовании источника данных. Чтобы разрешить имя, необходимо включить DNS-сервер пересылки.  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещаемой блокировки на объект ВНЕШНЕГО источника данных.  
  
##  <a name="examples"></a>Примеры: SQL Server 2016  
  
### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Создайте внешний источник данных к ссылке Hadoop  
Для создания внешнего источника данных для ссылки на Hortonworks или Cloudera Hadoop кластера, укажите имя компьютера или IP-адрес Hadoop Namenode и порт.  
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);

```  
  
### <a name="b-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>Б. Создайте внешний источник данных к ссылке Hadoop при включении включена  
Укажите параметр RESOURCE_MANAGER_LOCATION для включения принудительной передачи вычислений в Hadoop для обработки запросов PolyBase. После включения PolyBase используется решение на основе затрат для определения вычисление запроса должны быть переданы в Hadoop или перемещения всех данных для обработки запросов в SQL Server.
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
);

```
  
###  <a name="credential"></a> В. Создайте внешний источник данных для ссылки защитой Kerberos Hadoop  
Для проверки, если кластер Hadoop, защита Kerberos, проверьте значение свойства hadoop.security.authentication в Hadoop core-site.xml. Для ссылки защитой Kerberos кластеру, необходимо указать учетные данные уровня базы данных, содержащий Kerberos имя пользователя и пароль. Главный ключ базы данных используется для шифрования секрета учетных данных области базы данных. 
  
```sql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1 
WITH IDENTITY = '<hadoop_user_name>', 
SECRET = '<hadoop_password>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (
    TYPE = HADOOP, 
    LOCATION = 'hdfs://10.10.10.10:8050', 
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050', 
    CREDENTIAL = HadoopUser1
);
```

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>Г. Создайте внешний источник данных для ссылки на хранилище больших двоичных объектов
Для создания внешнего источника данных для ссылки контейнера хранилища BLOB-объектов Azure, укажите URI хранилища BLOB-объектов Azure и учетные данные уровня базы данных, содержащий ключ учетной записи хранилища Azure.

В этом примере к внешнему источнику данных представляет собой контейнер хранилища BLOB-объектов Azure, вызывается dailylogs под учетной записью хранилища Azure с именем myaccount. Хранилище Azure внешнего источника данных — для передачи данных. и не поддерживает включение предиката.

В этом примере показано, как создать учетные данные уровня базы данных для проверки подлинности в хранилище Azure. Укажите ключ учетной записи хранилища Azure в секретные учетные данные базы данных. Укажите идентификатор учетных данных, областью действия любую строку в базе данных, он не используется для проверки подлинности в хранилище Azure. Затем учетных данных используется в инструкции, которая создает внешний источник данных.

```
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
    TYPE = HADOOP, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```

## <a name="examples-azure-sql-database"></a>Примеры: База данных Azure SQL

### <a name="e-create-a-shard-map-manager-external-data-source"></a>Д. Создать источник внешних данных диспетчера карты сегментов
Для создания внешнего источника данных для ссылки на SHARD_MAP_MANAGER, укажите имя логического сервера, на котором размещена диспетчера карты сегментов в базе данных SQL Azure или базы данных SQL Server на виртуальной машине Azure.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = SHARD_MAP_MANAGER,
    LOCATION = '<server_name>.database.windows.net',
    DATABASE_NAME = 'ElasticScaleStarterKit_ShardMapManagerDb',
    CREDENTIAL = ElasticDBQueryCred,
    SHARD_MAP_NAME = 'CustomerIDShardMap'
);
```

### <a name="f-create-an-rdbms-external-data-source"></a>Е. Создание реляционной СУБД внешнего источника данных
Для создания внешнего источника данных для реляционной СУБД, ссылки на имя логического сервера удаленной базы данных в базе данных SQL Azure.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>';

CREATE DATABASE SCOPED CREDENTIAL SQL_Credential  
WITH IDENTITY = '<username>',
SECRET = '<password>';

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc 
WITH (
    TYPE = RDBMS, 
    LOCATION = '<server_name>.database.windows.net', 
    DATABASE_NAME = 'Customers', 
    CREDENTIAL = SQL_Credential 
);
```

## <a name="examples-azure-sql-data-warehouse"></a>Примеры: Хранилище данных Azure SQL

### <a name="g-create-external-data-source-to-reference-azure-data-lake-store"></a>Ж. Создайте внешний источник данных к ссылке хранилища Озера данных Azure
Подключение хранилища Озера данных Azure основан на ADLS URI и приложение Azure активные directory участника службы. Документация для создания этого приложения можно найти на[проверки подлинности хранилища Озера данных с помощью Active Directory](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory).

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLUser 
WITH IDENTITY = '<clientID>@<OAuth2.0TokenEndPoint>',
SECRET = '<KEY>' ;


CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH (TYPE = HADOOP,
      LOCATION = '<ADLS URI>'
)
```



## <a name="examples-parallel-data-warehouse"></a>Примеры: Параллельное хранилище данных

### <a name="h-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>З. Создайте внешний источник данных к ссылке Hadoop при включении включена
Укажите параметр JOB_TRACKER_LOCATION для включения принудительной передачи вычислений в Hadoop для обработки запросов PolyBase. После включения PolyBase используется решение на основе затрат для определения вычисление запроса должны быть переданы в Hadoop или перемещения всех данных для обработки запросов в SQL Server. 

```sql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    JOB_TRACKER_LOCATION = '10.10.10.10:8050'
);
```

### <a name="i-create-external-data-source-to-reference-azure-blob-storage"></a>И. Создайте внешний источник данных для ссылки на хранилище больших двоичных объектов
Для создания внешнего источника данных для ссылки контейнера хранилища BLOB-объектов Azure, укажите URI хранилища BLOB-объектов Azure в качестве внешних данных исходное МЕСТОПОЛОЖЕНИЕ. Добавление ключа учетной записи хранилища Azure PDW core-site.xml файл для проверки подлинности.

В этом примере к внешнему источнику данных представляет собой контейнер хранилища BLOB-объектов Azure, вызывается dailylogs под учетной записью хранилища Azure с именем myaccount. Источник внешних данных хранилища Azure для передачи данных только и не поддерживает включение предиката.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
        TYPE = HADOOP, 
        LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'
);
```

## <a name="examples-bulk-operations"></a>Примеры: Массовых операций   
### <a name="j-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>К. Создание внешнего источника данных для массовых операций, извлечение данных из хранилища больших двоичных объектов Azure.   
**Область применения:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].   
Используйте следующий источник данных с помощью массовых операций [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) или [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Учетные данные, используемые, должен быть создан с помощью `SHARED ACCESS SIGNATURE` с удостоверением. Дополнительные сведения о подписанных URL-адресах см. в [этой статье](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = AccessAzureInvoices
    );   
```   
В этом примере используется см. в разделе [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).
  
## <a name="see-also"></a>См. также
[Изменение ВНЕШНЕГО источника данных (Transact-SQL)](../../t-sql/statements/alter-external-data-source-transact-sql.md)  
[CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
[СОЗДАТЬ внешний TABLE AS SELECT &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[CREATE TABLE AS SELECT #40; Хранилище данных Azure SQL &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
[sys.external_data_sources (Transact-SQL)](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)  
  
  

