---
title: Настройка PolyBase для доступа к внешним данным в хранилище BLOB-объектов Azure | Документация Майкрософт
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: e7ac4cda37a211c73b9895bdface7e6ade56ad11
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874847"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Настройка PolyBase для доступа к внешним данным в хранилище BLOB-объектов Azure

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается использование PolyBase в экземпляре SQL Server для запроса внешних данных в хранилище BLOB-объектов Azure.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.

### <a name="configure-azure-blob-storage-connectivity"></a>Настройка подключения к хранилищу BLOB-объектов Azure

Сначала необходимо настроить SQL Server PolyBase для использования хранилища BLOB-объектов Azure.

1. Запустите [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md), задав для параметра hadoop connectivity значение поставщика хранилища BLOB-объектов Azure. Значение для поставщика см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md). По умолчанию для подключения к Hadoop установлено значение 7.

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Перезапустите SQL Server с помощью **services.msc**. При перезапуске SQL Server следующие службы также будут перезапущены:  

   - Служба перемещения данных SQL Server PolyBase  
   - Компонент SQL Server PolyBase Engine  
  
   ![остановка и запуск служб PolyBase в services.msc](../../relational-databases/polybase/media/polybase-stop-start.png "остановка и запуск служб PolyBase в services.msc")  
  
## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных Hadoop, необходимо определить внешнюю таблицу для использования в запросах Transact-SQL. Далее указаны шаги по настройке внешней таблицы.

1. Создайте главный ключ в базе данных. Это необходимо для шифрования секрета учетных данных.

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

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. Создайте формат внешнего файла с помощью инструкции [CREATE EXTERNAL FILE FORMAT](../../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE))  
   ```

1. Создайте внешнюю таблицу, указывающую на данные, хранящиеся в службе хранилища Azure, с помощью инструкции [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md). В этом примере внешние данные представляют собой данные датчика автомобиля.

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
  
- отправка нерегламентированных запросов к внешним таблицам;  
- импорт данных;  
- экспорт данных.  

Следующие запросы предоставляют пример с вымышленными данными датчика автомобиля.

### <a name="ad-hoc-queries"></a>Нерегламентированные запросы  

Следующий нерегламентированный запрос объединяет реляционные данные с данными Hadoop. Он выбирает клиентов, которые ездят быстрее 35 миль/ч, объединяя структурированные данные клиента, хранящиеся в SQL Server, с данными автомобильного датчика, хранящимися в Hadoop.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
```  

### <a name="importing-data"></a>импорт данных  

Следующий запрос позволяет импортировать внешние данные в SQL Server. В этом примере импортируются данные быстрых водителей в SQL Server для выполнения углубленного анализа. Для повышения производительности здесь используется технология columnstore.  

```sql
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

### <a name="exporting-data"></a>Экспорт данных  

Следующий запрос позволяет экспортировать данные из SQL Server в хранилище BLOB-объектов Azure. Чтобы сделать это, необходимо сначала включить экспорт PolyBase. Создайте внешнюю целевую таблицу, прежде чем экспортировать в нее данные.

```sql
-- Enable INSERT into external table  
sp_configure 'allow polybase export', 1;  
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

## <a name="view-polybase-objects-in-ssms"></a>Просмотр объектов PolyBase в SSMS  

В SSMS внешние таблицы отображаются в отдельной папке **Внешние таблицы**. Внешние источники данных и форматы внешних файлов находятся в папках, вложенных в папку **Внешние ресурсы**.  
  
![Объекты PolyBase в SSMS](media/polybase-management.png)  

## <a name="next-steps"></a>Следующие шаги

В следующих статьях приведены дополнительные сведения о способах использования и мониторинга PolyBase.

[Масштабируемые группы PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)  
[Устранение неполадок c PolyBase](polybase-troubleshooting.md)  
