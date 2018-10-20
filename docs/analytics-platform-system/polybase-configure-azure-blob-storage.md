---
title: Настраивать PolyBase для доступа к внешним данным в хранилище BLOB-объектов Azure | Документация Майкрософт
description: В этой статье описывается настройка PolyBase в Parallel Data Warehouse для подключения к внешней Hadoop.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7bbf2dface759da63bd6b9845f4e62321b1cbe76
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460638"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Настраивать PolyBase для доступа к внешним данным в хранилище BLOB-объектов Azure

Объясняется, как использовать PolyBase на экземпляре SQL Server для запроса внешних данных в хранилище BLOB-объектов Azure.

> [!NOTE]
> APS сейчас поддерживает только локально избыточное хранилище BLOB-объектов Azure (LRS) стандартный общего назначения версии 1.

## <a name="prerequisites"></a>предварительные требования

 - Хранилище BLOB-объектов в вашей подписке.
 - Контейнер, созданное в хранилище BLOB-объектов Azure.

### <a name="configure-azure-blob-storage-connectivity"></a>Настроить подключение к хранилищу BLOB-объектов Azure

Во-первых настройте APS использование хранилища BLOB-объектов Azure.

1. Запустите [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) с 'hadoop connectivity' присвоено с поставщиком хранилища больших двоичных объектов Azure. Значение для поставщика см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure Blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Перезапустите APS области, расположенные на странице состояния службы [устройства Configuration Manager](launch-the-configuration-manager.md).
  
## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные в хранилище больших двоичных объектов Azure, необходимо определить внешнюю таблицу для использования в запросах Transact-SQL. Далее указаны шаги по настройке внешней таблицы.

1. Создайте главный ключ в базе данных. Он необходим для шифрования секрета учетных данных.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

1. Создайте учетные данные уровня базы данных для хранилища BLOB-объектов Azure.

   ```sql
   -- IDENTITY: any string (this is not used for authentication to Azure storage).  
   -- SECRET: your Azure storage account key.  
   CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
   WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';
   ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md).

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. Создайте формат внешнего файла с помощью инструкции [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Azure Blob storage (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   -- In this example, the files are pipe (|) delimited
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

1. Создайте внешнюю таблицу, указывающую на данные, хранящиеся в службе хранилища Azure, с помощью инструкции [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). В этом примере внешние данные содержат данные датчиков автомобиля.

   ```sql
   -- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
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

1. Создайте статистику внешней таблицы.

   ```sql
   CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
   ```

## <a name="polybase-queries"></a>Запросы PolyBase

Есть три функции, которые выполняет PolyBase:  
  
- Нерегламентированные запросы к внешним таблицам.  
- импорт данных;  
- экспорт данных.  

Следующие запросы предоставляют пример с вымышленными данными датчика автомобиля.

### <a name="ad-hoc-queries"></a>Нерегламентированные запросы  

Следующий нерегламентированный запрос объединяет реляционные данные в хранилище BLOB-объектов Azure. Он выбирает клиентов, занимающихся разработкой быстрее, чем 35 миль/ч, присоединяемый структурированных клиента данные, хранящиеся в SQL Server, данные датчиков автомобиля, хранящиеся в хранилище BLOB-объектов Azure.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
```  

### <a name="importing-data"></a>импорт данных  

Следующий запрос выполняется Импорт внешних данных в APS. В этом примере импортирует данные для быстрого драйверов в точках доступа, чтобы выполнить более глубокий анализ. Для повышения производительности, при этом используется технология Columnstore в APS.  

```sql
CREATE TABLE Fast_Customers
WITH
(CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH (CustomerKey))
AS
SELECT DISTINCT
      Insured_Customers.CustomerKey, Insured_Customers.FirstName, Insured_Customers.LastName,   
      Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
from Insured_Customers INNER JOIN   
(  
      SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
```  

### <a name="exporting-data"></a>Экспорт данных  

Следующий запрос экспортирует данные из точек доступа в хранилище BLOB-объектов Azure. Он может использоваться для архивирования реляционных данных в BLOB-объектов Azure хранилища, оставаясь иметь возможность запросить его.

```sql
-- Export data: Move old data to Azure Blob storage while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = AzureStorage,  
      FILE_FORMAT = TextFileFormat
)  
AS
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  

## <a name="view-polybase-objects-in-ssdt"></a>Просмотреть объекты PolyBase в SSDT  

В SQL Server Data Tools, внешние таблицы отображаются в отдельной папке **внешние таблицы**. Внешние источники данных и форматы внешних файлов находятся в папках, вложенных в папку **Внешние ресурсы**.  
  
![Объекты PolyBase в SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в разделе [что такое PolyBase?](../relational-databases/polybase/polybase-guide.md). 

