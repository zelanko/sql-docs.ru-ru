---
title: Использование Polybase для доступа к внешним данным в хранилище BLOB-объектов Azure
description: Объясняется, как настроить Polybase в Parallel Data Warehouse для подключения к внешним Hadoop.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4ea61ea7e6983f9601783957eee6776f36eccfb4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400724"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Настройка Polybase для доступа к внешним данным в хранилище BLOB-объектов Azure

В этой статье объясняется, как использовать Polybase на экземпляре SQL Server для запроса внешних данных в хранилище BLOB-объектов Azure.

> [!NOTE]
> В настоящее время APS поддерживает только стандартное локально избыточное хранилище BLOB-объектов (LRS) общего назначения версии 1.

## <a name="prerequisites"></a>Предварительные требования

 - Хранилище BLOB-объектов Azure в вашей подписке.
 - Контейнер, созданный в хранилище BLOB-объектов Azure.

### <a name="configure-azure-blob-storage-connectivity"></a>Настройка подключения к хранилищу BLOB-объектов Azure

Во-первых, настройте ТД для использования хранилища BLOB-объектов Azure.

1. Запустите [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) с параметром "подключение Hadoop", установленным в поставщик хранилища BLOB-объектов Azure. Значение для поставщика см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure Blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Перезапустите регион APS с помощью страницы состояния службы [Configuration Manager устройства](launch-the-configuration-manager.md).
  
## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные в хранилище BLOB-объектов Azure, необходимо определить внешнюю таблицу, которая будет использоваться в запросах Transact — SQL. Далее указаны шаги по настройке внешней таблицы.

1. Создайте главный ключ в базе данных. Необходимо зашифровать секрет учетных данных.

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

1. Создайте внешнюю таблицу, указывающую на данные, хранящиеся в службе хранилища Azure, с помощью инструкции [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). В этом примере внешние данные представляют собой данные датчика автомобиля.

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

Следующий нерегламентированный запрос объединяет реляционные данные с данными в хранилище BLOB-объектов Azure. Он выбирает клиентов, которые работают быстрее, чем 35 миль/ч, объединяя структурированные данные клиентов, хранящиеся в SQL Server, с данными датчика автомобиля, хранящимися в хранилище BLOB-объектов Azure.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
```  

### <a name="importing-data"></a>импорт данных  

Следующий запрос импортирует внешние данные в ТД. В этом примере данные для быстрых драйверов импортируются в ТД для более глубокого анализа. Для повышения производительности она использует технологию columnstore в ТД.  

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

Следующий запрос экспортирует данные из ТД в хранилище BLOB-объектов Azure. Его можно использовать для архивации реляционных данных в хранилище BLOB-объектов Azure, в то же время сохраняя их возможность запрашивать.

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

## <a name="view-polybase-objects-in-ssdt"></a>Просмотр объектов Polybase в SSDT  

В SQL Server Data Tools внешние таблицы отображаются в отдельных папках **внешние таблицы**. Внешние источники данных и форматы внешних файлов находятся в папках, вложенных в папку **Внешние ресурсы**.  
  
![Объекты Polybase в SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в [этом руководстве](../relational-databases/polybase/polybase-guide.md). 

