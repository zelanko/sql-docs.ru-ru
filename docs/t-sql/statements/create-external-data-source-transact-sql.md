---
title: CREATE EXTERNAL DATA SOURCE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 04/01/2019
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
ms.openlocfilehash: 864c7b2da5b6b04f1c017997c3d1ecba31375b43
ms.sourcegitcommit: 02df4e7965b2a858030bb508eaf8daa9bc10b00b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265167"
---
# <a name="create-external-data-source-transact-sql"></a>CREATE EXTERNAL DATA SOURCE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Создает внешний источник данных для PolyBase или запросов эластичной базы данных. Внешние источники данных используются для обеспечения взаимодействия и поддерживают четыре основных варианта использования.

- Виртуализация и загрузка данных с помощью [PolyBase][intro_pb]
- Операции массовой загрузки в SQL Server или базе данных SQL с помощью `BULK INSERT` или `OPENROWSET`
- Запрос удаленных экземпляров базы данных SQL или хранилища данных SQL через базу данных SQL с помощью [эластичных запросов][remote_eq]
- Запрос сегментированной базы данных SQL Azure с помощью [эластичных запросов][sharded_eq]

> [!NOTE]  
> PolyBase поддерживается в SQL Server 2016 (или более поздней версии), хранилище данных SQL Azure и Parallel Data Warehouse. [Эластичные запросы][intro_eq] поддерживаются только в базе данных SQL Azure v12 или более поздней версии.

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Синтаксис  

```sql
CREATE EXTERNAL DATA SOURCE <data_source_name>  
WITH
(    LOCATION                  = '<prefix>://<path>[:<port>]'
[,   CONNECTION_OPTIONS        = '<name_value_pairs>']
[,   CREDENTIAL                = <credential_name> ]
[,   PUSHDOWN                  = ON | OFF]
[,   TYPE                      = HADOOP | BLOB_STORAGE | RDBMS | SHARD_MAP_MANAGER ]
[,   RESOURCE_MANAGER_LOCATION = '<resource_manager>[:<port>]']
[,   DATABASE_NAME             = '<database_name>' ]
[,   SHARD_MAP_NAME            = '<shard_map_manager>' ]
)
[;]
```

## <a name="arguments"></a>Аргументы

### <a name="datasourcename"></a>data_source_name

Задает определенное пользователем имя для источника данных. Имя должно быть уникальным в пределах базы данных в SQL Server, базе данных SQL Azure и хранилище данных SQL Azure. Имя должно быть уникальным в пределах сервера в Parallel Data Warehouse.

### <a name="location--prefixpathport"></a>LOCATION = *`'<prefix>://<path[:port]>'`*

Предоставляет протокол и путь подключения к внешнему источнику данных.

| Внешний источник данных        | Префикс расположения | Путь к расположению                                         | Поддерживаемые расположения по продукту или службе |
| --------------------------- | --------------- | ----------------------------------------------------- | ---------------------------------------- |
| Cloudera или Hortonworks     | `hdfs`          | `<Namenode>[:port]`                                   | SQL Server (2016+), PDW                  |
| хранилище BLOB-объектов Azure          | `wasb[s]`       | `<container>@<storage_account>.blob.core.windows.net` | SQL Server (2016+), PDW, SQL DW          |
| Azure Data Lake Store Gen 1 | `adl`           | `<storage_account>.azuredatalake.net`                 | SQL DW                                   |
| Azure Data Lake Store Gen 2 | `abfss`         | `<container>@<storage_account>.dfs.core.windows.net`  | SQL DW                                   |
| SQL Server                  | `sqlserver`     | `<server_name>[\<instance_name>][:port]`              | SQL Server (2019+)                       |
| Oracle;                      | `oracle`        | `<server_name>[:port]`                                | SQL Server (2019+)                       |
| Teradata                    | `teradata`      | `<server_name>[:port]`                                | SQL Server (2019+)                       |
| MongoDB или CosmosDB         | `mongodb`       | `<server_name>[:port]`                                | SQL Server (2019+)                       |
| интерфейс ODBC                        | `odbc`          | `<server_name>{:port]`                                | SQL Server (2019 +): только для Windows        |
| массовые операции             | `https`         | `<storage_account>.blob.core.windows.net/<container>` | SQL Server (2017+), SQL DB               |
| Эластичный запрос (сегмент)       | Не требуется    | `<shard_map_server_name>.database.windows.net`        | SQL DB                                   |
| Эластичный запрос (удаленный)      | Не требуется    | `<remote_server_name>.database.windows.net`           | SQL DB                                   |

Путь к расположению:

- `<`Namenode`>`: имя компьютера или IP-адрес `Namenode` в Hadoop Namenode. PolyBase необходимо разрешить любые DNS-имена, используемые в кластере Hadoop. <!-- For highly available Hadoop configurations, provide the Nameservice ID as the `LOCATION`. -->
- `port`: порт, который прослушивает внешний источник данных. В Hadoop порт можно найти, используя параметр конфигурации `fs.default.name`. Значение по умолчанию — 8020.
- `<container>`: контейнер учетной записи хранения, содержащей данные. Корневые контейнеры доступны только для чтения, записать данные в контейнер невозможно.
- `<storage_account>`: имя учетной записи хранения Azure.
- `<server_name>`: имя узла.
- `<instance_name>`: имя экземпляра SQL Server. Используется, если у вас работает служба обозревателя SQL Server на целевом экземпляре.
- `<shard_map_server_name>`: имя логического сервера в Azure, на котором размещен диспетчер карт сегментов. Аргумент `DATABASE_NAME` задает базу данных, в которой размещается карта сегментов, а `SHARD_MAP_NAME` используется для самой карты сегментов.
- `<remote_server_name>`: логическое имя целевого сервера для эластичного запроса. Имя базы данных задается с помощью аргумента `DATABASE_NAME`.

Дополнительные примечания и инструкции при задании расположения:

- Ядро SQL не проверяет существование внешнего источника данных, когда создает объект. Для проверки при создании внешней таблицы используйте внешний источник данных.
- Используйте один и тот же внешний источник данных для всех таблиц при запросе Hadoop, чтобы обеспечить согласованность семантики запросов.
- Можно использовать префикс расположения `sqlserver` для подключения SQL Server 2019 к SQL Server, базе данных SQL или хранилищу данных SQL.
- Укажите `Driver={<Name of Driver>}` при подключении через `ODBC`.
- `wasb` — протокол по умолчанию для хранилища больших двоичных объектов Azure. `wasbs` является необязательным, но рекомендуется, так как тогда данные будут передаваться по защищенному каналу SSL.
- Чтобы обеспечить успешное выполнение запросов PolyBase в случае отработки отказа Hadoop `Namenode`, целесообразно использовать для `Namenode` кластера Hadoop виртуальный IP-адрес. Если этого не сделать, следует выполнить команду [ALTER EXTERNAL DATA SOURCE][alter_eds], чтобы указать новое расположение.

### <a name="connectionoptions--keyvaluepair"></a>CONNECTION_OPTIONS = *пара "ключ-значение"*

Указывает дополнительные параметры при подключении через `ODBC` к внешнему источнику данных.

Имя драйвера необходимо, но существуют и другие параметры, такие как `APP='<your_application_name>'` или `ApplicationIntent= ReadOnly|ReadWrite`, которые полезно задать, так как они могут помочь в устранении неполадок.

См. в документации по продукту `ODBC` список разрешенных [CONNECTION_OPTIONS][connection_options]

### <a name="pushdown--on--off"></a>PUSHDOWN = *ON | OFF*

Указывает, могут ли вычисления быть переданы во внешний источник данных. Параметр включен по умолчанию.

`PUSHDOWN` поддерживается при подключении к SQL Server, Oracle, Teradata, MongoDB или ODBC на уровне внешнего источника данных.

Включение или отключение параметра на уровне запроса достигается за счет [указаний][hint_pb].

### <a name="credential--credentialname"></a>CREDENTIAL = *credential_name*

Задает учетные данные уровня базы данных для аутентификации во внешнем источнике данных.

Дополнительные примечания и инструкции при задании учетных данных:

- Чтобы загрузить данные из хранилища BLOB-объектов Azure или Azure Data Lake Store (ADLS) Gen 2 в хранилище данных SQL или PDW, используйте ключ хранилища Azure.
- `CREDENTIAL` требуется, только если большой двоичный объект был защищен. `CREDENTIAL` не является обязательным для наборов данных с возможностью анонимного доступа.
- При  = `BLOB_STORAGE``SHARED ACCESS SIGNATURE` учетные данные необходимо создавать, используя `TYPE` в качестве удостоверения. Кроме того, маркер SAS должен создаваться следующим образом:
  - Исключите начальные `?` при настройке в качестве секрета
  - Задайте по меньшей мере разрешение на чтение для файла, который требуется загрузить (например, `srt=o&sp=r`)
  - Используйте допустимый срок действия (все даты указываются в формате UTC).

Пример использования `CREDENTIAL` с `SHARED ACCESS SIGNATURE` и `TYPE` = `BLOB_STORAGE` см. в разделе [Создание внешнего источника данных для выполнения массовых операций и извлечения данных из хранилища BLOB-объектов Azure в базу данных SQL](#k-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage).

Сведения о создании учетных данных уровня базы данных см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc].

### <a name="type---hadoop--blobstorage--rdbms--shardmapmanager"></a>TYPE = *[ HADOOP | BLOB_STORAGE | RDBMS | SHARD_MAP_MANAGER]*

Указывает тип настраиваемого внешнего источника данных. Этот параметр требуется не всегда.

- Используйте HADOOP, если внешний источник данных — Cloudera, Hortonworks, хранилище BLOB-объектов Azure, ADLS Gen 1 или ADLS Gen 2.
- Используйте RDBMS для запросов между базами данных при использовании эластичных запросов из базы данных SQL.  
- Используйте SHARD_MAP_MANAGER при создании внешнего источника данных при подключении к сегментированной базе данных SQL.
- Используйте BLOB_STORAGE при выполнении пакетных операций с использованием инструкций [BULK INSERT][bulk_insert] или [OPENROWSET][openrowset] с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].

> [!IMPORTANT]
> Не устанавливайте `TYPE` при использовании любого другого источника внешних данных.

Пример использования `TYPE` = `HADOOP` для загрузки данных из хранилища BLOB-объектов Azure см. в разделе [Создание внешнего источника данных для ссылки на хранилище больших двоичных объектов](#e-create-external-data-source-to-reference-azure-blob-storage).

### <a name="resourcemanagerlocation--resourcemanageruriport"></a>RESOURCE_MANAGER_LOCATION = *'ResourceManager_URI[:порт]'*

Настройте это необязательное значение при подключении к Hortonworks или Cloudera.

Если `RESOURCE_MANAGER_LOCATION` определен, оптимизатор запросов будет принимать решение на основе затрат для повышения производительности. Задание MapReduce можно использовать, чтобы передать вычисления в Hadoop. Указание `RESOURCE_MANAGER_LOCATION` может значительно сократить объем данных, передаваемых между Hadoop и SQL, повышая производительность запросов.  

Если значение для Resource Manager не задано, отправка вычислений в Hadoop для запросов PolyBase отключена.

Если порт не задан, значение по умолчанию определяется с использованием текущей настройки для конфигурации подключения к Hadoop (hadoop connectivity).

| Подключение к Hadoop | Порт по умолчанию диспетчера ресурсов |
| ------------------- | ----------------------------- |
| 1                   | 50300                         |
| 2                   | 50300                         |
| 3                   | 8021                          |
| 4                   | 8032                          |
| 5                   | 8050                          |
| 6                   | 8032                          |
| 7                   | 8050                          |

Полный список поддерживаемых версий Hadoop см. в разделе [Конфигурация подключений PolyBase (Transact-SQL)][connectivity_pb].

> [!IMPORTANT]  
> Значение RESOURCE_MANAGER_LOCATION не проверяется при создании внешнего источника данных. Указание неверного значения может вызвать сбой запроса во время выполнения каждый раз, когда выполняется попытка принудительной передачи, так как переданное значение невозможно разрешить.

См. конкретный пример и дальнейшие рекомендации в разделе [Создание внешнего источника данных для ссылки на Hadoop с поддержкой передачи](#c-create-external-data-source-to-reference-hadoop-with-push-down-enabled).

### <a name="databasename--databasename"></a>DATABASE_NAME = *имя базы данных*

Настройте этот аргумент, если `TYPE` задан как `RDBMS` или `SHARD_MAP_MANAGER`.

| TYPE              | Значение DATABASE_NAME                                       |
| ----------------- | ------------------------------------------------------------ |
| СУРБД             | Имя удаленной базы данных на сервере, заданном с помощью `LOCATION` |
| SHARD_MAP_MANAGER | Имя базы данных, работающей в качестве диспетчера карты сегментов      |

Пример, демонстрирующий создание внешнего источника данных с `TYPE` = `RDBMS`, см. в разделе [Создание внешнего источника данных в реляционной СУБД](#g-create-an-rdbms-external-data-source).

### <a name="shardmapname--shardmapname"></a>SHARD_MAP_NAME = *имя карты сегментов*

Используется, только когда аргумент `TYPE` имеет значение `SHARD_MAP_MANAGER`, для того, чтобы задать имя карты сегментов.

Пример, демонстрирующий создание внешнего источника данных с `TYPE` = `SHARD_MAP_MANAGER`, см. в разделе [Создание диспетчера карты сегментов в реляционной СУБД](#f-create-a-shard-map-manager-external-data-source).

## <a name="permissions"></a>Разрешения

Необходимо разрешение CONTROL на базу данных в SQL Server, Parallel Data Warehouse, базе данных SQL и хранилище данных SQL.

> [!NOTE]
> В предыдущих выпусках PDW для создания внешнего источника данных требовались разрешения ALTER ANY EXTERNAL DATA SOURCE.

## <a name="locking"></a>Блокировка

Принимает совмещенную блокировку на объекте EXTERNAL DATA SOURCE.  

## <a name="security"></a>безопасность

PolyBase поддерживает проверку подлинности на основе прокси-сервера для большинства внешних источников данных. Создайте учетные данные уровня базы данных для создания учетной записи-посредника.

При подключении к хранилищу или пулу данных в кластере больших данных SQL Server учетные данные пользователя передаются через серверную систему. Создайте имена входа в пуле данных, чтобы включить сквозную проверку подлинности.

Сейчас маркер SAS с типом `HADOOP` не поддерживается. Он поддерживается только с ключом доступа учетной записи хранения. Попытка создать внешний источник данных с типом `HADOOP` и использованием учетных данных SAS может завершиться сбоем со следующим сообщением об ошибке:

`Msg 105019, Level 16, State 1 - EXTERNAL TABLE access failed due to internal error: 'Java exception raised on call to HdfsBridge_Connect. Java exception message: Parameters provided to connect to the Azure storage account are not valid.: Error [Parameters provided to connect to the Azure storage account are not valid.] occurred while accessing external file.'`

## <a name="examples-sql-server-2016-and-parallel-data-warehouse"></a>Примеры: SQL Server (2016+) и Parallel Data Warehouse

### <a name="a-create-external-data-source-in-sql-2019-to-reference-oracle"></a>A. Создание внешнего источника данных в SQL 2019 для ссылки на Oracle

Чтобы создать внешний источник данных, ссылающийся на Oracle, убедитесь, что у вас есть учетные данные уровня базы данных. При необходимости также может включить или отключить передачу вычислений к этому источнику данных.

```sql
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '!MyC0mpl3xP@ssw0rd!
;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL OracleProxyAccount
WITH
     IDENTITY   = 'oracle_username'
,    SECRET     = 'oracle_password'
;

CREATE EXTERNAL DATA SOURCE MyOracleServer
WITH
(    LOCATION   = 'oracle://145.145.145.145:1521'
,    CREDENTIAL = OracleProxyAccount
,    PUSHDOWN   = ON
;
```

Дополнительные примеры для других источников данных, таких как MongoDB, см. в разделе [Настройка PolyBase для доступа к внешним данным в MongoDB][mongodb_pb].

### <a name="b-create-external-data-source-to-reference-hadoop"></a>Б. Создание внешнего источника данных для ссылки на Hadoop

Чтобы создать внешний источник данных для ссылки на кластер Hadoop Hortonworks или Cloudera Hadoop, укажите имя компьютера или IP-адрес `Namenode` и порта Hadoop. <!-- Provide the Nameservice ID as the `LOCATION` for highly available configurations. -->

```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION = 'hdfs://10.10.10.10:8050'
,    TYPE     = HADOOP
)
;
```

### <a name="c-create-external-data-source-to-reference-hadoop-with-push-down-enabled"></a>В. Создание внешнего источника данных для ссылки на Hadoop с включенной отправкой

Укажите параметр `RESOURCE_MANAGER_LOCATION`, чтобы включить принудительную передачу вычислений в Hadoop для запросов PolyBase. После включения PolyBase принимает решение на основе затрат для определения того, должны ли вычисления запроса быть переданы в Hadoop.

```sql  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION                  = 'hdfs://10.10.10.10:8020'
,    TYPE                      = HADOOP
,    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
)
;
```

### <a name="d-create-external-data-source-to-reference-kerberos-secured-hadoop"></a>Г. Создание внешнего источника данных для ссылки на Hadoop с защитой Kerberos

Чтобы проверить, защищен ли кластер Hadoop протоколом Kerberos, проверьте значение свойства hadoop.security.authentication в файле Hadoop core-site.xml. Чтобы сослаться на кластер Hadoop с защитой Kerberos, необходимо указать учетные данные с областью действия "база данных", которые содержат ваше имя пользователя и пароль Kerberos. Главный ключ базы данных используется для шифрования секрета учетных данных с областью действия "база данных".

```sql  
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Kerberos user name and password.
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
WITH
     IDENTITY   = '<hadoop_user_name>'
,    SECRET     = '<hadoop_password>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyHadoopCluster
WITH
(    LOCATION                  = 'hdfs://10.10.10.10:8050'
,    CREDENTIAL                = HadoopUser1
,    TYPE                      = HADOOP
,    RESOURCE_MANAGER_LOCATION = '10.10.10.10:8050'
)
;
```

## <a name="examples-sql-server-2016-sql-data-warehouse-and-parallel-data-warehouse"></a>Примеры: SQL Server (2016+), хранилище данных SQL и Parallel Data Warehouse

### <a name="e-create-external-data-source-to-reference-azure-blob-storage"></a>Д. Создание внешнего источника данных для ссылки на хранилище BLOB-объектов Azure

В этом примере внешний источник данных представляет собой контейнер хранилища BLOB-объектов Azure под названием `daily` в учетной записи хранения Azure с именем `logs`. Внешний источник данных хранилища Azure предназначен исключительно для передачи данных, отправка предиката не поддерживается.

В этом примере показано, как создать учетные данные с областью действия "база данных" для аутентификации в хранилище Azure. Укажите ключ учетной записи хранения Azure в секрете учетных данных базы данных. Укажите любую строку в удостоверении учетных данных с областью действия "база данных"; для проверки подлинности в хранилище Azure эти данные не используются.

```sql
-- Create a database master key if one does not already exist, using your own password. This key is used to encrypt the credential secret in next step.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo'
;

-- Create a database scoped credential with Azure storage account key as the secret.
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
WITH
     IDENTITY   = '<my_account>'
,    SECRET     = '<azure_storage_account_key>'
;

-- Create an external data source with CREDENTIAL option.
CREATE EXTERNAL DATA SOURCE MyAzureStorage
WITH
(    LOCATION   = 'wasbs://daily@logs.blob.core.windows.net/'
,    CREDENTIAL = AzureStorageCredential
,    TYPE       = HADOOP
)
;
```

## <a name="examples-sql-database"></a>Примеры: База данных SQL

### <a name="f-create-a-shard-map-manager-external-data-source"></a>Е. Создание внешнего источника данных для диспетчера карт сегментов

Чтобы создать внешний источник данных, ссылающийся на SHARD_MAP_MANAGER, укажите имя сервера базы данных SQL, на котором размещен диспетчер карт сегментов в базе данных SQL, или базу данных SQL Server на виртуальной машине.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

CREATE DATABASE SCOPED CREDENTIAL ElasticDBQueryCred
WITH
     IDENTITY   = '<username>'
,    SECRET     = '<password>'
;

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc
WITH
(    TYPE             = SHARD_MAP_MANAGER
,    LOCATION         = '<server_name>.database.windows.net'
,    DATABASE_NAME    = 'ElasticScaleStarterKit_ShardMapManagerDb'
,    CREDENTIAL       = ElasticDBQueryCred
,    SHARD_MAP_NAME   = 'CustomerIDShardMap'
)
;
```

Пошаговое руководство см. в разделе [Приступая к работе с эластичными запросами для сегментирования (горизонтальное секционирование)][sharded_eq_tutorial].

### <a name="g-create-an-rdbms-external-data-source"></a>Ж. Создание внешнего источника данных RDBMS

Чтобы создать внешний источник данных для ссылки на RDBMS, указывается имя сервера базы данных SQL удаленной базы данных в базе данных SQL.

```sql
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

CREATE DATABASE SCOPED CREDENTIAL SQL_Credential  
WITH
     IDENTITY  = '<username>'
,    SECRET    = '<password>'
;

CREATE EXTERNAL DATA SOURCE MyElasticDBQueryDataSrc
WITH
(    TYPE          = RDBMS
,    LOCATION      = '<server_name>.database.windows.net'
,    DATABASE_NAME = 'Customers'
,    CREDENTIAL    = SQL_Credential
)
;
```

Пошаговое руководство по RDBMS см. в разделе [Начало работы с запросами между базами данных (вертикальное секционирование)][remote_eq_tutorial].

## <a name="examples-sql-data-warehouse"></a>Примеры: Хранилище данных SQL

### <a name="h-create-external-data-source-to-reference-azure-data-lake-store-gen-1"></a>З. Создание внешнего источника данных для ссылки на хранилище Azure Data Lake Store Gen 1

Для подключения Azure Data Lake Store используется универсальный код ресурса (URI) ADLS и субъект-служба приложения в Azure Active Directory. Документация по созданию этого приложения доступна в разделе [Аутентификация хранилища озера данных с помощью Active Directory][azure_ad[].

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLS_credential
WITH
--   IDENTITY   = '<clientID>@<OAuth2.0TokenEndPoint>'
     IDENTITY   = '536540b4-4239-45fe-b9a3-629f97591c0c@https://login.microsoftonline.com/42f988bf-85f1-41af-91ab-2d2cd011da47/oauth2/token'
--,  SECRET     = '<KEY>'
,    SECRET     = 'BjdIlmtKp4Fpyh9hIvr8HJlUida/seM5kQ3EpLAmeDI='
;
CREATE EXTERNAL DATA SOURCE AzureDataLakeStore
WITH
(    LOCATION       = 'adl://newyorktaxidataset.azuredatalakestore.net'
,    CREDENTIAL     = ADLS_credential
,    TYPE           = HADOOP
)
;
```

### <a name="i-create-external-data-source-to-reference-azure-data-lake-store-adls-gen-2"></a>И. Создание внешнего источника данных для ссылки на хранилище Azure Data Lake Store (ADLS) Gen 2

Для подключения к ADLS Gen 2 требуется ключ учетной записи хранения в качестве секрета учетных данных области базы данных. В настоящее время поддержка OAuth 2.0 недоступна.

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

-- These values come from your Azure Active Directory Application used to authenticate to ADLS
CREATE DATABASE SCOPED CREDENTIAL ADLS_credential
WITH
--   IDENTITY   = '<storage_account_name>'
     IDENTITY   = 'newyorktaxidata'
--,  SECRET     = '<storage_account_key>'
,    SECRET     = 'yz5N4+bxSb89McdiysJAzo+9hgEHcJRJuXbF/uC3mhbezES/oe00vXnZEl14U0lN3vxrFKsphKov16C0w6aiTQ=='
;

CREATE EXTERNAL DATA SOURCE <data_source_name>
WITH
(    LOCATION   = 'abfss://2013@newyorktaxidataset.dfs.core.windows.net'
,    CREDENTIAL = ADLS_credential
,    TYPE       = HADOOP
)
[;]
```

### <a name="j-create-external-data-source-to-reference-azure-data-lake-store-adls-gen-2-or-azure-blob-storage-with-managed-identities"></a>К. Создание внешнего источника данных для ссылки на хранилище Azure Data Lake Store (ADLS) 2-го поколения или хранилище BLOB-объектов Azure с управляемыми удостоверениями

Следуйте [инструкциям](https://docs.microsoft.com/azure/sql-data-warehouse/load-data-from-azure-blob-storage-using-polybase#authenticate-using-managed-identities-to-load-optional) по регистрации и настройке доступа RBAC к серверу SQL Server перед созданием учетных данных для базы данных.  

```sql
-- If you do not have a Master Key on your DW you will need to create one.
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<password>'
;

-- There is no need to specify SECRET because this mechanism uses Managed Identity under the covers.
CREATE DATABASE SCOPED CREDENTIAL ADLS_credential
WITH
     IDENTITY   = 'Managed Service Identity'
;

CREATE EXTERNAL DATA SOURCE <data_source_name>
WITH
(    LOCATION   = 'abfss://2013@newyorktaxidataset.dfs.core.windows.net'
,    CREDENTIAL = ADLS_credential
,    TYPE       = HADOOP
)
[;]
```

## <a name="examples-bulk-operations"></a>Примеры: массовые операции

> [!NOTE]
> Не следует помещать **/** , имя файла или параметры подписи общего доступа в конце URL-адреса `LOCATION` при настройке внешнего источника данных для массовых операций.

### <a name="k-create-an-external-data-source-for-bulk-operations-retrieving-data-from-azure-blob-storage"></a>Л. Создание внешнего источника данных для массовых операций, извлекающих данные из хранилища BLOB-объектов Azure

**Применимо к:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].
Используйте следующий источник данных для массовых операций, выполняемых с использованием инструкций [BULK INSERT][bulk_insert] или [OPENROWSET][openrowset]. Используемые учетные данные должны задавать `SHARED ACCESS SIGNATURE` в качестве идентификатора, не должны иметь `?` в начале маркера SAS, должны иметь по крайней мере разрешение на чтение загружаемого файла (например, `srt=o&sp=r`), и иметь допустимый срок действия (все даты должны быть указаны в формате UTC). Дополнительные сведения о подписанных URL-адресах см. в статье [Использование подписанных URL-адресов][sas_token].

```sql
CREATE DATABASE SCOPED CREDENTIAL AccessAzureInvoices
WITH
     IDENTITY = 'SHARED ACCESS SIGNATURE'
--   REMOVE ? FROM THE BEGINNING OF THE SAS TOKEN
,    SECRET = '******srt=sco&sp=rwac&se=2017-02-01T00:55:34Z&st=2016-12-29T16:55:34Z***************'
;

CREATE EXTERNAL DATA SOURCE MyAzureInvoices
WITH
(    LOCATION   = 'https://newinvoices.blob.core.windows.net/week3'
,    CREDENTIAL = AccessAzureInvoices
,    TYPE       = BLOB_STORAGE
)
;
```

Реализация этого примера доступна в разделе [BULK INSERT][bulk_insert_example].

## <a name="see-also"></a>См. также:

- [ALTER EXTERNAL DATA SOURCE (Transact-SQL)][alter_eds]
- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)][create_dsc]
- [CREATE EXTERNAL FILE FORMAT (Transact-SQL)][create_eff]
- [CREATE EXTERNAL TABLE (Transact-SQL)][create_etb]
- [CREATE EXTERNAL TABLE AS SELECT (хранилище данных SQL Azure)][create_etb_as_sel]
- [CREATE TABLE AS SELECT (хранилище данных SQL Azure)][create_tbl_as_sel]
- [sys.external_data_sources (Transact-SQL)][cat_eds]
- [Использование подписанных URL-адресов][sas_token]
- [Общие сведения об эластичных запросах][intro_eq]

<!-- links to external pages -->
<!-- SQL Docs -->
[bulk_insert]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql
[bulk_insert_example]: https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql#f-importing-data-from-a-file-in-azure-blob-storage
[openrowset]: https://docs.microsoft.com/sql/t-sql/functions/openrowset-transact-sql

[create_dsc]: https://docs.microsoft.com/sql/t-sql/statements/create-database-scoped-credential-transact-sql
[create_eff]: https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql
[create_etb]: https://docs.microsoft.com/sql/t-sql/statements/create-external-table-transact-sql
[create_etb_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-external-table-as-select-transact-sql?view=azure-sqldw-latest
[create_tbl_as_sel]: https://docs.microsoft.com/sql/t-sql/statements/create-table-as-select-azure-sql-data-warehouse?view=azure-sqldw-latest

[alter_eds]: https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql

[cat_eds]: https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-external-data-sources-transact-sql
<!-- PolyBase docs -->
[intro_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide
[mongodb_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-configure-mongodb
[connectivity_pb]:https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql
[connection_options]: https://docs.microsoft.com/sql/relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client
[hint_pb]: https://docs.microsoft.com/sql/relational-databases/polybase/polybase-pushdown-computation#force-pushdown
<!-- Elastic Query Docs -->
[intro_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/
[remote_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[remote_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started-vertical/
[sharded_eq]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/
[sharded_eq_tutorial]: https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-getting-started/

<!-- Azure Docs -->
[azure_ad]: https://docs.microsoft.com/azure/data-lake-store/data-lake-store-authenticate-using-active-directory
[sas_token]: https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1
