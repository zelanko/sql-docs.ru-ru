---
title: Настройка PolyBase для доступа к внешним данным в Hadoop | Документация Майкрософт
description: В этой статье описывается настройка PolyBase в Parallel Data Warehouse для подключения к внешней Hadoop.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b0a49925ec0d0592adfd131e0ab994e5e8356f95
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236940"
---
# <a name="configure-polybase-to-access-external-data-in-hadoop"></a>Настройка PolyBase для доступа к внешним данным в Hadoop

Объясняется, как использовать PolyBase на устройство APS для запроса внешних данных в Hadoop.

## <a name="prerequisites"></a>предварительные требования

PolyBase поддерживает два поставщика Hadoop — Hortonworks Data Platform (HDP) и Cloudera Distributed Hadoop (CDH). В новых выпусках Hadoop соблюдается шаблон "Основной номер версии.дополнительный номер версии.версия". Также поддерживаются все версии в рамках поддерживаемых основного и дополнительного выпусков. Поддерживаются следующие поставщики Hadoop:
 - Hortonworks HDP 1.3 в ОС Linux или Windows Server;  
 - Hortonworks HDP 2.1–2.6 в Linux
 - Hortonworks HDP 2.1–2.3 в ОС Windows Server;  
 - Cloudera CDH 4.3 в Linux;  
 - Cloudera CDH 5.1–5.5, 5.9–5.13 в Linux;

### <a name="configure-hadoop-connectivity"></a>Настройка подключения к Hadoop

Во-первых настройте APS для использования конкретного поставщика Hadoop.

1. Запустите [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) с hadoop connectivity и задайте соответствующее значение для поставщика. Значение для поставщика см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md). 

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Перезапустите APS области, расположенные на странице состояния службы [устройства Configuration Manager](launch-the-configuration-manager.md).
  
## <a id="pushdown"></a> Активация вычислений pushdown  

Чтобы улучшить производительность при выполнении запроса, активируйте вычисление pushdown для кластера Hadoop.  
  
1. Откройте удаленный рабочий стол для узла управления PDW.

2. Найдите файл **yarn-site.xml** в управляющем узле. Как правило, путь выглядит следующим образом:  

   ```xml  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\  
   ```  

3. Найдите аналогичный файл на компьютере с Hadoop в каталоге конфигурации. Открыв его, найдите и скопируйте значение ключа конфигурации yarn.application.classpath.  
  
4. На узле управления в **файла yarn.site.xml** найти **yarn.application.classpath** свойство. Вставьте значение, скопированное на компьютере с Hadoop, в качестве значения элемента.  
  
5. Для всех версий CDH 5.X необходимо добавить параметры конфигурации mapreduce.application.classpath либо в конец файла yarn.site.xml, либо в файл mapred-site.xml. HortonWorks содержит эти настройки в конфигурациях yarn.application.classpath. Примеры см. в статье [Конфигурация PolyBase](../relational-databases/polybase/polybase-configuration.md).

## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных Hadoop, необходимо определить внешнюю таблицу для использования в запросах Transact-SQL. Далее указаны шаги по настройке внешней таблицы.

1. Создайте главный ключ в базе данных. Он необходим для шифрования секрета учетных данных.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

2. Создайте учетные данные на уровне базы данных для кластеров Hadoop, защищенных с помощью Kerberos.

   ```sql
   -- IDENTITY: the Kerberos user name.  
   -- SECRET: the Kerberos password  
   CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
   WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
   ```

3. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md).

   ```sql
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

4. Создайте формат внешнего файла с помощью инструкции [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

5. Создайте внешнюю таблицу, указывающую на данные, хранящиеся в Hadoop, с помощью инструкции [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). В этом примере внешние данные содержат данные датчиков автомобиля.

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
         DATA_SOURCE = MyHadoopCluster,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

6. Создайте статистику внешней таблицы.

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

Следующий нерегламентированный запрос объединяет реляционные с данными Hadoop. Он выбирает клиентов, занимающихся разработкой быстрее, чем 35 миль/ч, присоединяемый клиента структурированные данные, хранящиеся в APS, данные датчиков автомобиля, хранящиеся в Hadoop.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
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

Следующий запрос экспортирует данные из APS Hadoop. Он может использоваться для архивации реляционных данных в Hadoop время по-прежнему иметь возможность запрашивать его.

```sql
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = HadoopHDP2,  
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

См. в разделе параметров безопасности Hadoop [настроить безопасность Hadoop](polybase-configure-hadoop-security.md).<br>
Дополнительные сведения о PolyBase см. в [этом руководстве](../relational-databases/polybase/polybase-guide.md). 
 
