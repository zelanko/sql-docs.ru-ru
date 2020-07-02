---
title: sp_estimate_data_compression_savings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/26/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs:
- TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 04201e9127f5de173767f7b2071088f2bd4f2828
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772174"
---
# <a name="sp_estimate_data_compression_savings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает текущий размер запрошенного объекта и оценивает размер объекта для запрошенного состояния сжатия. Сжатие можно оценить для всех таблиц или только для части. Сюда входят кучи, кластеризованные индексы, некластеризованные индексы, индексы columnstore, индексированные представления, а также секции таблиц и индексов. Объекты могут быть сжаты с помощью сжатия строк, страниц, columnstore или columnstore архива. Если таблица, индекс или секция уже сжаты, использование этой процедуры позволяет определить размер таблицы, индекса или секции в распакованном виде.  
  
> [!NOTE]
> Сжатие и **sp_estimate_data_compression_savings** доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Чтобы оценить размер объекта после сжатия с запрошенными параметрами, эта хранимая процедура создает образец исходного объекта и загружает эти данные в эквивалентную таблицу и индекс, созданные в базе данных tempdb. Созданная в базе данных tempdb таблица или индекс затем сжимается до необходимых настроек, и вычисляется оценка экономии от сжатия.  
  
 Чтобы изменить состояние сжатия таблицы, индекса или секции, используйте инструкции [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) . Общие сведения о сжатии см. в разделе [Сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
> [!NOTE]  
> Если существующие данные фрагментированы, можно уменьшить их размер без использования сжатия, перестроив индекс. Для индексов коэффициент заполнения будет применен во время перестроения индекса. Это может увеличить размер индекса.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [ @index_id = ] index_id   
   , [ @partition_number = ] partition_number   
   , [ @data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @schema_name =] "*schema_name*"  
 Имя схемы базы данных, содержащей таблицу или индексированное представление. *schema_name* имеет тип **sysname**. Если *schema_name* имеет значение null, используется схема по умолчанию текущего пользователя.  
  
 [ @object_name =] "*object_name*"  
 Имя таблицы или индексированного представления, к которым относится индекс. Аргумент *object_name* имеет тип **sysname**.  
  
 [ @index_id =] *index_id*  
 Идентификатор индекса. *index_id* имеет **тип int**и может принимать одно из следующих значений: идентификационный номер индекса, null или 0, если *object_id* является кучей. Чтобы вернуть данные для всех индексов базовой таблицы или представления, укажите значение NULL. Если указано значение NULL, необходимо также указать значение NULL для *partition_number*.  
  
 [ @partition_number =] *partition_number*  
 Номер секции в объекте. *partition_number* имеет **тип int**и может принимать одно из следующих значений: номер секции индекса или кучи, null или 1 для несекционированного индекса или кучи.  
  
 Чтобы указать секцию, можно также указать функцию [$Partition](../../t-sql/functions/partition-transact-sql.md) . Чтобы получить сведения обо всех секциях объекта, укажите значение NULL.  
  
 [ @data_compression =] "*DATA_COMPRESSION*"  
 Тип сжатия для оценки. *DATA_COMPRESSION* может принимать одно из следующих значений: None, Row, Page, COLUMNSTORE или COLUMNSTORE_ARCHIVE.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Приведенный ниже результирующий набор содержит сведения о текущем и предполагаемом размере таблицы, индекса или секции.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|Имя таблицы или индексированного представления.|  
|schema_name|**sysname**|Схема таблицы или индексированного представления.|  
|index_id|**int**|Идентификатор индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = некластеризованный индекс|  
|partition_number|**int**|Номер секции. Возвращает 1 для несекционированной таблицы или индекса.|  
|size_with_current_compression_setting (КБ)|**bigint**|Размер запрошенной таблицы, индекса или секции в текущем состоянии.|  
|size_with_requested_compression_setting (КБ)|**bigint**|Предполагаемый размер таблицы, индекса или секции при использовании запрошенных настроек сжатия, и, если применимо, существующего коэффициента заполнения при отсутствии фрагментации.|  
|sample_size_with_current_compression_setting (КБ)|**bigint**|Размер образца с текущими настройками сжатия. К этим настройкам относится любая фрагментация.|  
|sample_size_with_requested_compression_setting (КБ)|**bigint**|Размер образца, созданного с использованием запрошенных настроек сжатия, и, если применимо, существующего коэффициента заполнения при отсутствии фрагментации.|  
  
## <a name="remarks"></a>Примечания  
 Используется `sp_estimate_data_compression_savings` для оценки экономии, которая может возникнуть при включении таблицы или секции для сжатия архива строк, страниц, columnstore или columnstore. Например, если средний размер строки можно уменьшить на 40%, то размер самого объекта также можно потенциально уменьшить на 40%. Но выигрыша можно не получить, поскольку экономия места зависит от коэффициента заполнения и размера строки. Например, если имеется строка размером 8 000 байт и уменьшение ее размера на 40 процентов, можно по-прежнему разместить только одну строку на странице данных. При этом экономия отсутствует.  
  
 Если результаты выполнения хранимой процедуры `sp_estimate_data_compression_savings` показывают, что размер таблицы будет увеличиваться, это означает, что в таблице используется почти полная точность типов данных, а небольшой объем затрат, необходимый для использования сжатого формата, превышает экономию места от самого сжатия. В этом редком случае сжатие включать не следует.  
  
 Если для таблицы разрешено сжатие, использование процедуры `sp_estimate_data_compression_savings` позволяет оценить средний размер строки распакованной таблицы.  
  
 Во время этой операции для таблицы необходима блокировка (IS). Если блокировку (IS) получить невозможно, процедура блокируется. Таблица просматривается с уровнем изоляции read committed.  
  
 Если запрошенные настройки сжатия совпадают с текущими, хранимая процедура возвращает ожидаемый размер без фрагментации данных с текущим коэффициентом заполнения.  
  
 Если индекс или идентификатор секции не существует, результат не возвращается.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `SELECT` для таблицы.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 До SQL Server 2019 эта процедура не была применена к индексам columnstore и поэтому не принимает параметры сжатия данных COLUMNSTORE и COLUMNSTORE_ARCHIVE.  Начиная с SQL Server 2019, индексы columnstore можно использовать как в качестве исходного объекта для оценки, так и в качестве требуемого типа сжатия.

 > [!IMPORTANT]
 > Если [метаданные tempdb, оптимизированные для памяти](../databases/tempdb-database.md#memory-optimized-tempdb-metadata) , включены в [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] , создание индексов columnstore во временных таблицах не поддерживается. Из-за этого ограничения sp_estimate_data_compression_savings не поддерживаются с параметрами сжатия данных COLUMNSTORE и COLUMNSTORE_ARCHIVE, если включены метаданные TempDB, оптимизированные для памяти.

## <a name="considerations-for-columnstore-indexes"></a>Рекомендации для индексов columnstore
 Начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] , `sp_estimate_compression_savings` поддерживает оценку сжатия архива columnstore и columnstore. В отличие от сжатия страниц и строк, применение сжатия columnstore к объекту требует создания нового индекса columnstore. По этой причине при использовании параметров COLUMNSTORE и COLUMNSTORE_ARCHIVE этой процедуры тип исходного объекта, предоставляемого для процедуры, определяет тип индекса COLUMNSTORE, используемого для оценки сжатого размера. В следующей таблице показаны ссылочные объекты, используемые для оценки сжатия каждого типа исходного объекта, если @data_compression для параметра задано значение COLUMNSTORE или COLUMNSTORE_ARCHIVE.

 |Исходный объект|Ссылочный объект|
 |-----------------|---------------|
 |Куча|Кластеризованный индекс columnstore|
 |Кластеризованный индекс|Кластеризованный индекс columnstore|
 |Некластеризованный индекс|Некластеризованный индекс columnstore (включая ключевые столбцы и все включенные столбцы предоставленного некластеризованного индекса, а также столбец секционирования таблицы, если таковые имеются)|
 |некластеризованный индекс columnstore|Некластеризованный индекс columnstore (включая те же столбцы, что и предоставленный некластеризованный индекс columnstore)|
 |Кластеризованный индекс columnstore|Кластеризованный индекс columnstore|

> [!NOTE]  
> При оценке сжатия columnstore из исходного объекта rowstore (кластеризованный индекс, некластеризованный индекс или куча), если в исходном объекте есть какие-либо столбцы, имеющие тип данных, не поддерживаемый в индексе columnstore, sp_estimate_compression_savings завершится ошибкой.

 Аналогично, если `@data_compression` параметру присвоено значение `NONE` , `ROW` или, `PAGE` а исходный объект является индексом columnstore, то в следующей таблице описаны используемые ссылочные объекты.

 |Исходный объект|Ссылочный объект|
 |-----------------|---------------|
 |Кластеризованный индекс columnstore|Куча|
 |некластеризованный индекс columnstore|Некластеризованный индекс (включая столбцы, содержащиеся в некластеризованном индексе columnstore в качестве ключевых столбцов, и столбец секционирования таблицы, если таковые имеются, в качестве включенного столбца).|

> [!NOTE]  
> При оценке сжатия rowstore (NONE, ROW или PAGE) из исходного объекта columnstore убедитесь, что исходный индекс не содержит более 32 столбцов, так как это ограничение, поддерживаемое в rowstore (некластеризованном) индексе.
  
## <a name="examples"></a>Примеры  
 В следующем примере оценивается размер таблицы `Production.WorkOrderRouting` в случае сжатия `ROW`.  
  
```sql  
USE AdventureWorks2016;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [sys. partitions &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Реализация сжатия Юникода](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
