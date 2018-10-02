---
title: CREATE EXTERNAL DATA SOURCE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL DATA SOURCE
- CREATE_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, data source
- PolyBase, create data source
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39dd5cf772bebf66f8d2a5e827badf4ef0981b66
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708742"
---
# <a name="create-external-data-source-transact-sql"></a>CREATE EXTERNAL DATA SOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Создает внешний источник данных для PolyBase или запросов эластичной базы данных. В зависимости от сценария синтаксис существенно отличается. Внешний источник данных, созданный для PolyBase, не может использоваться для запросов эластичной базы данных.  Аналогичным образом внешний источник данных, созданный для запросов эластичной базы данных, не может использоваться для PolyBase и т. д. 
  
> [!NOTE]  
>  PolyBase поддерживается только в SQL Server 2016 (или более поздней версии), хранилище данных SQL Azure и Parallel Data Warehouse. Запросы эластичной базы данных поддерживаются только в базе данных SQL Azure v12 или более поздней версии.  
  
 Для сценариев PolyBase внешним источником данных является системный файл Hadoop (HDFS), контейнер BLOB-объектов Azure или хранилище озера данных Azure. Дополнительные сведения см. в разделе [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 Для сценариев с запросами эластичной базы данных внешним источником является либо диспетчер карт сегментов (в базе данных SQL Azure), либо удаленная база данных (в базе данных SQL Azure).  Используйте инструкцию[sp_execute_remote (база данных SQL Azure)](../../relational-databases/system-stored-procedures/sp-execute-remote-azure-sql-database.md) после создания внешнего источника данных. Дополнительные сведения см. в разделе [Запрос эластичной базы данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/).  

  Внешний источник данных "Хранилище BLOB-объектов Azure" поддерживает синтаксис `BULK INSERT` и `OPENROWSET` и отличается от хранилища BLOB-объектов Azure для PolyBase.
    
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
-- (on SQL Server 2016)  
CREATE EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
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
        TYPE = BLOB_STORAGE,
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
 *data_source_name* задает определенное пользователем имя для источника данных. Имя должно быть уникальным в пределах базы данных в SQL Server, базы данных SQL Azure и хранилища данных SQL Azure. Имя должно быть уникальным в пределах сервера в Parallel Data Warehouse.
  
 TYPE = [ HADOOP | SHARD_MAP_MANAGER | RDBMS | BLOB_STORAGE]  
 Задает тип источника данных. Используйте HADOOP, если внешним источником данных является Hadoop или хранилище BLOB-объектов Azure для Hadoop. Используйте SHARD_MAP_MANAGER при создании внешнего источника данных для запроса эластичной базы данных с целью сегментирования базы данных SQL Azure. Используйте RDBMS с внешними источниками данных для запросов между базами данных с запросом эластичной базы данных в базе данных SQL Azure.  Используйте BLOB_STORAGE при выполнении пакетных операций с использованием инструкций [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) или [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
  
LOCATION = \<location_path> **HADOOP**    
Для HADOOP: указывает универсальный код ресурса (URI) для кластера Hadoop.  
`LOCATION = 'hdfs:\/\/*NameNode\_URI*\[:*port*\]'`  
NameNode_URI: имя компьютера или IP-адрес кластера Hadoop Namenode.  
порт: порт IPC Namenode. Это указывается в параметре конфигурации fs.default.name в Hadoop. Если значение не указано, по умолчанию будет использоваться 8020.  
Пример: `LOCATION = 'hdfs://10.10.10.10:8020'`

Для хранилища BLOB-объектов Azure с Hadoop задает URI для подключения к хранилищу BLOB-объектов Azure.  
`LOCATION = 'wasb[s]://container@account_name.blob.core.windows.net'`  
wasb[s]: задает протокол для хранилища BLOB-объектов Azure. Знак [s] является необязательным и указывает на безопасное подключение SSL: данные, отправляемые с SQL Server, надежно зашифрованы с помощью протокола SSL. Настоятельно рекомендуется использовать wasbs вместо wasb. Обратите внимание, что расположение может использовать asv[s] вместо wasb[s]. Синтаксис asv[s] является устаревшим и будет упразднен в следующем выпуске.  
container: задает имя контейнера хранилища BLOB-объектов Azure. Чтобы указать корневой контейнер учетной записи хранения в домене, используйте имя домена, а не имя контейнера. Корневые контейнеры доступны только для чтения, записать данные в контейнер невозможно.  
account_name: полное доменное имя (FQDN) учетной записи хранения Azure.  
Пример: `LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'`

Для хранилища озера данных Azure местоположение указывает URI для подключения к хранилищу озера данных Azure.



**SHARD_MAP_MANAGER**   
 Для SHARD_MAP_MANAGER: указывает имя логического сервера, на котором размещен диспетчер карт сегментов в базе данных SQL Azure или базе данных SQL Server на виртуальной машине Azure.
 
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

Пошаговое руководство см. в разделе [Приступая к работе с эластичными запросами для сегментирования (горизонтальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/).
  
**RDBMS**   
Для RDBMS: задает имя логического сервера удаленной базы данных в базе данных SQL Azure.  

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
  
Пошаговое руководство по RDBMS см. в разделе [Начало работы с запросами между базами данных (вертикальное секционирование)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/).  

**BLOB_STORAGE**   
Только для массовых операций: `LOCATION` должно быть действительным URL-адресом хранилища BLOB-объектов Azure или контейнера. Не помещайте **/**, имя файла или параметры подписи общего доступа в конце URL-адреса `LOCATION`.   
Используемые учетные данные необходимо создавать, используя `SHARED ACCESS SIGNATURE` в качестве удостоверения. Дополнительные сведения о подписанных URL-адресах см. в статье [Использование подписанных URL-адресов](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1). Пример доступа к хранилищу BLOB-объектов см. в примере Ж инструкции [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md). 
>[!NOTE] 
>Для загрузки из хранилища BLOB-объектов Azure в хранилище данных SQL или Parallel Data Warehouse в качестве секретного ключа необходимо использовать ключ хранилища Azure.

  
 RESOURCE_MANAGER_LOCATION = '*ResourceManager_URI*[:*port*]'  
 Задает расположение диспетчера ресурсов Hadoop. Если значение задано, оптимизатор запросов может принимать решение о предварительной обработке данных для запроса PolyBase с учетом затрат ресурсов, используя вычислительные возможности Hadoop вместе с MapReduce. Оно называется передачей предиката и может значительно сократить объем данных, передаваемых между Hadoop и SQL, повышая производительность запросов.  
  
 Если значение не задано, отправка вычислений в Hadoop для запросов PolyBase отключена.  
 
Если порт не задан, значение по умолчанию определяется с использованием текущей настройки для конфигурации подключения к Hadoop (hadoop connectivity).

|Подключение к Hadoop|Порт по умолчанию диспетчера ресурсов|
|-------------------|-----------------------------|
|1|50300|
|2|50300|
|3|8021|
|4|8032|
|5|8050|
|6|8032|
|7|8050|

Полный список распределений и версий Hadoop, поддерживаемых каждым значением подключения, см. в разделе [Конфигурация подключения PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).
  
> [!IMPORTANT]  
>  Значение RESOURCE_MANAGER_LOCATION — это строка, она не проверяется при создании внешнего источника данных. При вводе неверного значения возможны дополнительные задержки при осуществлении доступа к расположению.  
  
 Примеры Hadoop:  
  
-   Hortonworks HDP 2.0, 2.1, 2.2. 2.3 в Windows:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
-   Hortonworks HDP 1.3 в Windows:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:50300'  
    ```  
  
-   Hortonworks HDP 2.0, 2.1, 2.2, 2.3 в Linux:   
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
  
-   Cloudera 5.1–5.11 в Linux:   
    ```  
    RESOURCE_MANAGER_LOCATION = 'ResourceManager_URI:8032'  
    ```  
  
 CREDENTIAL = *credential_name*  
 Задает учетные данные уровня базы данных для аутентификации во внешнем источнике данных. Например, см. пример [В. Создание внешнего источника данных хранилища BLOB-объектов Azure](../../t-sql/statements/create-external-data-source-transact-sql.md#credential). Чтобы создать учетные данные, см. раздел [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md). Обратите внимание, что CREDENTIAL не требуются для общедоступных наборов данных с возможностью анонимного доступа. 
  
 DATABASE_NAME = *'QueryDatabaseName'*  
 Имя базы данных, которое работает в качестве диспетчера карт сегментов (для SHARD_MAP_MANAGER) или удаленной базы данных (для RDBMS).  
  
 SHARD_MAP_NAME = *'ShardMapName'*  
 Только для SHARD_MAP_MANAGER. Имя карты сегментов. Дополнительные сведения о создании карты сегментов см. в разделе [Начало работы с запросами эластичных баз данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/)  
  
## <a name="polybase-specific-notes"></a>Заметки о PolyBase  
Полный список поддерживаемых внешних источников данных см. в разделе [Конфигурация подключений PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

 Для использования PolyBase необходимо создать следующие три объекта:  
  
-   Внешний источник данных.  
  
-   Формат внешнего файла и  
  
-   Внешняя таблица, ссылающаяся на внешний источник данных и формат внешнего файла.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL для базы данных в SQL DW, SQL Server, APS 2016 и SQL DB.

> [!IMPORTANT]  
>  В предыдущих выпусках PDW для создания внешнего источника данных требовались разрешения ALTER ANY EXTERNAL DATA SOURCE.
  
  
## <a name="error-handling"></a>Обработка ошибок  
 Если разрешение RESOURCE_MANAGER_LOCATION во внешних источниках данных Hadoop определено несогласованно, происходит ошибка выполнения. То есть невозможно задать два внешних источника данных, ссылающихся на один и тот же кластер Hadoop, а затем предоставить расположение диспетчера ресурсов только для одного из них.  
  
 Ядро SQL не проверяет существование внешнего источника данных, когда создает объект внешнего источника данных. Если источник данных не существует во время выполнения запроса, происходит ошибка.  
  
## <a name="general-remarks"></a>Общие замечания  
Для PolyBase внешний источник данных в SQL Server и хранилище данных SQL имеет область действия "база данных". В параллельном хранилище данных областью действия является сервер.
  
Для PolyBase: если определен параметр RESOURCE_MANAGER_LOCATION или JOB_TRACKER_LOCATION, оптимизатор запросов оценит целесообразность оптимизации каждого запроса, инициировав задание map reduce во внешнем источнике Hadoop и передав вычисления. Это решение принимается исключительно на основе стоимости ресурсов.  

Чтобы обеспечить успешное выполнение запросов PolyBase в случае отработки отказа Hadoop NameNode, целесообразно использовать для NameNode кластера Hadoop виртуальный IP-адрес. Если не использовать виртуальный IP-адрес для Hadoop NameNode, в случае отработки отказа Hadoop NameNode потребуется использовать разрешение ALTER EXTERNAL DATA SOURCE, чтобы указать на новое расположение.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Все источники данных, определенные в одном и том же расположении кластера Hadoop, должны использовать один и тот же параметр для RESOURCE_MANAGER_LOCATION или JOB_TRACKER_LOCATION. Если существует несоответствие, возникнет ошибка выполнения.  
  
 Если кластер Hadoop настроен с именем, а внешний источник данных использует для указания на расположение кластера IP-адрес, PolyBase все равно должна иметь возможность разрешить имя кластера при использовании источника данных. Чтобы разрешить имя, необходимо включить DNS-сервер пересылки.  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещенную блокировку на объекте EXTERNAL DATA SOURCE.  
  
##  <a name="examples"></a> Примеры: SQL Server 2016  
  
### <a name="a-create-external-data-source-to-reference-hadoop"></a>A. Создание внешнего источника данных для ссылки на Hadoop  
Чтобы создать внешний источник данных для ссылки на кластер Hadoop Hortonworks или Cloudera Hadoop, укажите имя компьютера или IP-адрес узла имен и порта Hadoop.  
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8050'
);

```  
  
### <a name="b-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>Б. Создание внешнего источника данных для ссылки на Hadoop с включенной отправкой  
Укажите параметр RESOURCE_MANAGER_LOCATION, чтобы включить принудительную передачу вычислений в Hadoop для запросов PolyBase. После включения этой функции PolyBase принимает решение на основе стоимости ресурсов, чтобы определить, нужно ли отправлять вычисления запроса в Hadoop или для обработки запроса в SQL Server нужно перенести все данные.
  
```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
);

```
  
###  <a name="credential"></a> В. Создание внешнего источника данных для ссылки на Hadoop с защитой Kerberos  
Чтобы проверить, защищен ли кластер Hadoop протоколом Kerberos, проверьте значение свойства hadoop.security.authentication в файле Hadoop core-site.xml. Чтобы сослаться на кластер Hadoop с защитой Kerberos, необходимо указать учетные данные с областью действия "база данных", которые содержат ваше имя пользователя и пароль Kerberos. Главный ключ базы данных используется для шифрования секрета учетных данных с областью действия "база данных". 
  
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

### <a name="d-create-external-data-source-to-reference-azure-blob-storage"></a>Г. Создание внешнего источника данных для ссылки на хранилище BLOB-объектов Azure
Чтобы создать внешний источник данных, ссылающийся на контейнер хранилища BLOB-объектов Azure, укажите URI хранилища BLOB-объектов Azure и учетные данные с областью действия "база данных", содержащие ваш ключ учетной записи хранения Azure.

В этом примере внешний источник данных представляет собой контейнер хранилища BLOB-объектов Azure под названием dailylogs в учетной записи хранения Azure с именем myaccount. Внешний источник данных хранилища Azure предназначен исключительно для передачи данных, отправка предиката не поддерживается.

В этом примере показано, как создать учетные данные с областью действия "база данных" для аутентификации в хранилище Azure. Укажите ключ учетной записи хранения Azure в секрете учетных данных базы данных. Укажите любую строку в удостоверении учетных данных с областью действия "база данных", для аутентификации в хранилище Azure эти данные не используются. Затем эти учетные данные используются в инструкции, которая создает внешний источник данных.

```
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential 
WITH IDENTITY = 'myaccount', 
SECRET = '<azure_storage_account_key>';

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
    TYPE = BLOB_STORAGE, 
    LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/',
    CREDENTIAL = AzureStorageCredential
);
```

## <a name="examples-azure-sql-database"></a>Примеры: база данных SQL Azure

### <a name="e-create-a-shard-map-manager-external-data-source"></a>Д. Создание внешнего источника данных для диспетчера карт сегментов
Чтобы создать внешний источник данных, ссылающийся на SHARD_MAP_MANAGER, укажите имя логического сервера, на котором размещен диспетчер карт сегментов в базе данных SQL Azure, или базу данных SQL Server на виртуальной машине Azure.

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

### <a name="f-create-an-rdbms-external-data-source"></a>Е. Создание внешнего источника данных RDBMS
Чтобы создать внешний источник данных для ссылки на RDBMS, указывается имя логического сервера удаленной базы данных в базе данных SQL Azure.

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

## <a name="examples-azure-sql-data-warehouse"></a>Примеры: хранилище данных SQL Azure

### <a name="g-create-external-data-source-to-reference-azure-data-lake-store"></a>Ж. Создание внешнего источника данных для ссылки на хранилище озера данных Azure
Для подключения хранилища озера данных Azure используется URI ADLS и принцип обслуживания приложения в Azure Active Directory. Документация по созданию этого приложения доступна в разделе [Аутентификация хранилища озера данных с помощью Active Directory](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory).

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



## <a name="examples-parallel-data-warehouse"></a>Примеры: параллельное хранилище данных

### <a name="h-create-external-data-source-to-reference-hadoop-with-pushdown-enabled"></a>З. Создание внешнего источника данных для ссылки на Hadoop с включенной отправкой
Укажите параметр JOB_TRACKER_LOCATION, чтобы включить принудительную передачу вычислений в Hadoop для запросов PolyBase. После включения этой функции PolyBase принимает решение на основе стоимости ресурсов, чтобы определить, нужно ли отправлять вычисления запроса в Hadoop или для обработки запроса в SQL Server нужно перенести все данные. 

```sql
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH (
    TYPE = HADOOP,
    LOCATION = 'hdfs://10.10.10.10:8020',
    JOB_TRACKER_LOCATION = '10.10.10.10:8050'
);
```

### <a name="i-create-external-data-source-to-reference-azure-blob-storage"></a>И. Создание внешнего источника данных для ссылки на хранилище BLOB-объектов Azure
Для создания внешнего источника данных, ссылающегося на контейнер хранилища BLOB-объектов Azure, укажите URI хранилища BLOB-объектов Azure в качестве параметра LOCATION внешнего источника данных. Добавьте ключ учетной записи хранения Azure в файл PDW core-site.xml для аутентификации.

В этом примере внешний источник данных представляет собой контейнер хранилища BLOB-объектов Azure под названием dailylogs в учетной записи хранения Azure с именем myaccount. Внешний источник данных хранилища Azure предназначен исключительно для передачи данных, отправка предиката не поддерживается.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureStorage WITH (
        TYPE = HADOOP, 
        LOCATION = 'wasbs://dailylogs@myaccount.blob.core.windows.net/'
);
```

## <a name="examples-bulk-operations"></a>Примеры: массовые операции   
### <a name="j-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>К. Создание внешнего источника данных для массовых операций, извлекающих данные из хранилища BLOB-объектов Azure.   
**Применимо к:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].   
Используйте следующий источник данных для массовых операций, выполняемых с использованием инструкций [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) или [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Используемые учетные данные необходимо создавать, используя `SHARED ACCESS SIGNATURE` в качестве удостоверения. Дополнительные сведения о подписанных URL-адресах см. в статье [Использование подписанных URL-адресов](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).   
```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH  (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = AccessAzureInvoices
    );   
```   
Реализация этого примера доступна в разделе [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).
  
## <a name="see-also"></a>См. также:
[ALTER EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/alter-external-data-source-transact-sql.md)  
[CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
[CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
[CREATE EXTERNAL TABLE AS SELECT (Transact-SQL)](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
[CREATE TABLE AS SELECT (хранилище данных SQL Azure)](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)  
[sys.external_data_sources (Transact-SQL)](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)  
  
  

