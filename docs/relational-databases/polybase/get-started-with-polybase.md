---
title: Приступая к работе с PolyBase | Документация Майкрософт
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: get-started-article
helpviewer_keywords:
- PolyBase
- PolyBase, getting started
- Hadoop import
- Hadoop export
- Azure blob storage import
- Azure blob storage export
- Hadoop import, PolyBase getting started
- Hadoop export, Polybase getting started
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4542219cc2597ed86157a41e22ebeb8b25b9945b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233934"
---
# <a name="get-started-with-polybase"></a>Приступая к работе с PolyBase
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе содержатся основные сведения о запуске PolyBase на экземпляре SQL Server.
  
 Выполнив приведенные ниже действия, вы получите такой результат:  
  
-   на вашем сервере будет установлена и готова к запуску технология PolyBase;  
  
-   у вас будут примеры инструкций, создающих объекты PolyBase;  
  
-   вы узнаете, как управлять объектами PolyBase в SQL Server Management Studio (SSMS);  
  
-   у вас будут примеры запросов, в которых используются объекты PolyBase.    

## <a name="install-polybase"></a>Установка PolyBase  
Если вы не установили PolyBase, см. раздел [Установка PolyBase](../../relational-databases/polybase/polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.
  
### <a name="how-to-confirm-installation"></a>Подтверждение установки  
 Чтобы после установки убедиться, что технология PolyBase успешно установлена, выполните приведенную ниже команду. Если служба PolyBase установлена, она возвращает значение 1, а если нет — значение 0.  
  
```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
##  <a name="supported"></a> Настройка PolyBase  
 После установки необходимо настроить SQL Server для использования либо вашей версии Hadoop, либо хранилища больших двоичных объектов. PolyBase поддерживает два поставщика Hadoop — Hortonworks Data Platform (HDP) и Cloudera Distributed Hadoop (CDH).  Вот некоторые из поддерживаемых внешних источников данных:  
  
-   Hortonworks HDP 1.3 в ОС Linux или Windows Server;  
  
-   Hortonworks HDP 2.1–2.6 в Linux

-   Hortonworks HDP 2.1–2.3 в ОС Windows Server;  
  
-   Cloudera CDH 4.3 в Linux;  
  
-   Cloudera CDH 5.1–5.5, 5.9–5.13 в Linux;  
  
-   хранилище BLOB-объектов Azure.  
 
В новых выпусках Hadoop соблюдается шаблон "Основной.Дополнительный.Версия". Поддерживаются все версии в рамках поддерживаемых основного и дополнительного выпусков.
 

>  [!NOTE]
> Подключение Azure Data Lake Store поддерживается только в хранилище данных SQL Azure.
  
### <a name="external-data-source-configuration"></a>Конфигурация внешнего источника данных  
  
1.  Запустите хранимую процедуру [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 'hadoop connectivity' и задайте соответствующее значение. По умолчанию для подключения Hadoop установлено значение 7. Значение см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
      ```sql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  Перезапустите SQL Server с помощью **services.msc**. При перезапуске SQL Server следующие службы также будут перезапущены:  
  
    -   Служба перемещения данных SQL Server PolyBase  
  
    -   Компонент SQL Server PolyBase Engine  
  
 ![остановка и запуск служб PolyBase в services.msc](../../relational-databases/polybase/media/polybase-stop-start.png "остановка и запуск служб PolyBase в services.msc")  
  
### <a name="pushdown-configuration"></a>Конфигурация Pushdown  
 Чтобы улучшить производительность при выполнении запроса, активируйте вычисление Pushdown для кластера Hadoop.  
  
1.  Найдите файл **yarn-site.xml** в каталоге установки SQL Server. Как правило, путь выглядит следующим образом:  
  
    ```  
  
    C:Program FilesMicrosoft SQL ServerMSSQL13.MSSQLSERVERMSSQLBinnPolybaseHadoopconf  
  
    ```  
  
2.  Найдите аналогичный файл на компьютере с Hadoop в каталоге конфигурации. Открыв его, найдите и скопируйте значение ключа конфигурации yarn.application.classpath.  
  
3.  На компьютере SQL Server в файле **yarn.site.xml** найдите свойство **yarn.application.classpath** . Вставьте значение, скопированное на компьютере с Hadoop, в качестве значения элемента.  
  
4. Для всех версий CDH 5.X необходимо добавить параметры конфигурации mapreduce.application.classpath либо в конец файла yarn.site.xml, либо в файл mapred-site.xml. HortonWorks содержит эти настройки в конфигурациях yarn.application.classpath. Примеры см. в статье [Конфигурация PolyBase](../../relational-databases/polybase/polybase-configuration.md).

 
## <a name="scale-out-polybase"></a>Масштабирование PolyBase  
 Группы PolyBase позволяют создавать кластеры экземпляров SQL Server для обработки больших наборов данных из внешних источников данных, используя возможности масштабирования. Это помогает повысить производительность запросов.  
  
1.  Установите SQL Server с PolyBase на нескольких компьютерах.  
  
2.  Выберите один из серверов SQL Server в качестве головного узла.  
  
3.  Добавьте остальные экземпляры в качестве вычислительных узлов с помощью [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
4.  Перезапустите службу перемещения данных PolyBase на вычислительных узлах.  
  
 Подробные сведения см. в разделе [Масштабируемые группы PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).  
  
## <a name="create-t-sql-objects"></a>Создание объектов T-SQL  
 Создайте объекты в зависимости от внешнего источника данных (Hadoop или хранилище Azure).  
  
### <a name="hadoop"></a>Hadoop  
  
```sql  
-- 1: Create a database scoped credential.  
-- Create a master key on the database. This is required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- 2: Create a database scoped credential  for Kerberos-secured Hadoop clusters.  
-- IDENTITY: the Kerberos user name.  
-- SECRET: the Kerberos password  
  
CREATE DATABASE SCOPED CREDENTIAL HadoopUser1   
WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
  
-- 3:  Create an external data source.  
-- LOCATION (Required) : Hadoop Name Node IP address and port.  
-- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
-- CREDENTIAL (Optional):  the database scoped credential, created above.  
  
CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
        TYPE = HADOOP,   
        LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',   
        RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',   
        CREDENTIAL = HadoopUser1        
);  
  
-- 4: Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).    
CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
        FORMAT_TYPE = DELIMITEDTEXT,   
        FORMAT_OPTIONS (FIELD_TERMINATOR ='|',   
                USE_TYPE_DEFAULT = TRUE)  
  
-- 5:  Create an external table pointing to data stored in Hadoop.  
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
  
-- 6:  Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
### <a name="azure-blob-storage"></a>хранилище BLOB-объектов Azure.  
  
```sql  
--1: Create a master key on the database.  
-- Required to encrypt the credential secret.  
  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
  
-- Create a database scoped credential  for Azure blob storage.  
-- IDENTITY: any string (this is not used for authentication to Azure storage).  
-- SECRET: your Azure storage account key.  
  
CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential   
WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';  
  
--2:  Create an external data source.  
-- LOCATION:  Azure account storage account name and blob container name.  
-- CREDENTIAL: The database scoped credential created above.  
  
CREATE EXTERNAL DATA SOURCE AzureStorage with (  
        TYPE = HADOOP,   
        LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
        CREDENTIAL = AzureStorageCredential  
);  
  
--3:  Create an external file format.  
-- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).  
  
CREATE EXTERNAL FILE FORMAT TextFileFormat
WITH (  
       FORMAT_TYPE = DELIMITEDTEXT,   
       FORMAT_OPTIONS (
         FIELD_TERMINATOR ='|',   
         USE_TYPE_DEFAULT = TRUE
       )
);
         
  
--4: Create an external table.  
-- The external table points to data stored in Azure storage.  
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
  
--5: Create statistics on an external table.   
CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
  
```  
  
## <a name="polybase-queries"></a>Запросы PolyBase  
 Есть три функции, которые выполняет PolyBase:  
  
-   отправка нерегламентированных запросов к внешним таблицам;  
  
-   импорт данных;  
  
-   экспорт данных.  
  
### <a name="query-examples"></a>Примеры запросов  
  
-   Нерегламентированные запросы  
  
    ```sql  
    -- PolyBase Scenario 1: Ad-Hoc Query joining relational with Hadoop data   
    -- Select customers who drive faster than 35 mph: joining structured customer data stored   
    -- in SQL Server with car sensor data stored in Hadoop.  
    SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,   
            Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
    FROM Insured_Customers, CarSensor_Data  
    WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35   
    ORDER BY CarSensor_Data.Speed DESC  
    OPTION (FORCE EXTERNALPUSHDOWN);    -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
    ```  
  
-   импорт данных  
  
    ```sql  
    -- PolyBase Scenario 2: Import external data into SQL Server.  
    -- Import data for fast drivers into SQL Server to do more in-depth analysis and  
    -- leverage Columnstore technology.  
  
    SELECT DISTINCT   
            Insured_Customers.FirstName, Insured_Customers.LastName,   
            Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
    INTO Fast_Customers from Insured_Customers INNER JOIN   
    (  
            SELECT * FROM CarSensor_Data where Speed > 35   
    ) AS SensorD  
    ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
    ORDER BY YearlyIncome  
  
    CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
    ```  
  
-   Экспорт данных  
  
    ```  
    -- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
  
    -- Enable INSERT into external table  
    sp_configure ‘allow polybase export’, 1;  
    reconfigure  
  
    -- Create an external table.   
    CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
            [FirstName] char(25) NOT NULL,   
            [LastName] char(25) NOT NULL,   
            [YearlyIncome] float NULL,   
            [MaritalStatus] char(1) NOT NULL  
    )  
    WITH (  
            LOCATION='/old_data/2009/customerdata',  
            DATA_SOURCE = HadoopHDP2,  
            FILE_FORMAT = TextFileFormat,  
            REJECT_TYPE = VALUE,  
            REJECT_VALUE = 0  
    );  
  
    -- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
    INSERT INTO dbo.FastCustomer2009  
    SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
    ON (T1.CustomerKey = T2.CustomerKey)  
    WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
    ```  
  
## <a name="managing-polybase-objects-in-ssms"></a>Управление объектами PolyBase в SSMS  
 В SSMS внешние таблицы отображаются в отдельной папке **Внешние таблицы**. Внешние источники данных и форматы внешних файлов находятся в папках, вложенных в папку **Внешние ресурсы**.  
  
 ![объекты PolyBase в SSMS](../../relational-databases/polybase/media/polybase-management.png "объекты PolyBase в SSMS")  
  
## <a name="troubleshooting"></a>Устранение неполадок  
 Используйте динамические административные представления для устранения неполадок производительности и запросов. Подробные сведения см. в разделе [Устранение неполадок c PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md).  
  
 После обновления с версии-кандидата 1 SQL Server 2016 до версии-кандидата 2 или 3 запросы могут завершаться сбоем. Подробные сведения и описание решения см. в [заметках о выпуске SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md) , выполнив поиск по запросу "PolyBase".  
  
## <a name="next-steps"></a>Следующие шаги  
 Чтобы получить сведения о функции масштабирования, см. раздел [Масштабируемые группы PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).  Сведения о наблюдении за PolyBase см. в разделе [Устранение неполадок c PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md). См. дополнительные сведения ведения об [устранении неполадок производительности PolyBase с использованием динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80).  
  
## <a name="see-also"></a>См. также:  
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)   
 [Масштабируемые группы PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)   
 [PolyBase stored procedures](http://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)  (Хранимые процедуры PolyBase)  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
