---
title: "sp_estimate_data_compression_savings (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs: TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 80b5cb7fff9bfadd2d1dfe03884d2e723744fe8b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spestimatedatacompressionsavings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает текущий размер запрошенного объекта и оценивает размер объекта для запрошенного состояния сжатия. Сжатие можно оценить для всех таблиц или только для части. Это же касается куч, кластеризованных и некластеризованных индексов, индексированных представлений, табличных и индексных секций. Объекты могут быть сжаты с помощью сжатия строк или сжатия страниц. Если таблица, индекс или секция уже сжаты, использование этой процедуры позволяет определить размер таблицы, индекса или секции в распакованном виде.  
  
> [!NOTE]  
>  Сжатие и **sp_estimate_data_compression_savings** доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Чтобы оценить размер объекта после сжатия с запрошенными параметрами, эта хранимая процедура создает образец исходного объекта и загружает эти данные в эквивалентную таблицу и индекс, созданные в базе данных tempdb. Созданная в базе данных tempdb таблица или индекс затем сжимается до необходимых настроек, и вычисляется оценка экономии от сжатия.  
  
 Чтобы изменить состояние сжатия таблицы, индекса или секции, используйте [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) инструкции. Общие сведения о сжатии см. в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
> [!NOTE]  
>  Если существующие данные фрагментированы, можно уменьшить их размер без использования сжатия, перестроив индекс. Для индексов коэффициент заполнения будет применен во время перестроения индекса. Это может увеличить размер индекса.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [@index_id = ] index_id   
   , [@partition_number = ] partition_number   
   , [@data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @schema_name=] '*schema_name*"  
 Имя схемы базы данных, содержащей таблицу или индексированное представление. *schema_name* — **sysname**. Если *schema_name* имеет значение NULL, используется схема по умолчанию текущего пользователя.  
  
 [ @object_name=] '*object_name*"  
 Имя таблицы или индексированного представления, к которым относится индекс. *object_name* — **sysname**.  
  
 [ @index_id=] '*index_id*"  
 Идентификатор индекса. *index_id* — **int**, и может принимать одно из следующих значений: идентификатор индекса, NULL или 0, если *object_id* является кучей. Чтобы вернуть данные для всех индексов базовой таблицы или представления, укажите значение NULL. Если указать значение NULL, необходимо также указать значение NULL для *partition_number*.  
  
 [ @partition_number=] '*partition_number*"  
 Номер секции в объекте. *partition_number* — **int**, и может принимать одно из следующих значений: номер секции индекса или кучи, NULL или 1 для несекционированного индекса или кучи.  
  
 Чтобы указать раздел, можно также указать [$partition](../../t-sql/functions/partition-transact-sql.md) функции. Чтобы получить сведения обо всех секциях объекта, укажите значение NULL.  
  
 [ @data_compression=] '*data_compression*"  
 Тип сжатия для оценки. *data_compression* может принимать одно из следующих значений: NONE, строки или страницы.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Приведенный ниже результирующий набор содержит сведения о текущем и предполагаемом размере таблицы, индекса или секции.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|Имя таблицы или индексированного представления.|  
|schema_name|**sysname**|Схема таблицы или индексированного представления.|  
|index_id|**int**|Идентификатор индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = некластеризованный индекс|  
|partition_number|**int**|Номер секции. Возвращает 1 для несекционированной таблицы или индекса.|  
|size_with_current_compression_setting (КБ)|**bigint**|Размер запрошенной таблицы, индекса или секции в текущем состоянии.|  
|size_with_requested_compression_setting (КБ)|**bigint**|Предполагаемый размер таблицы, индекса или секции при использовании запрошенных настроек сжатия, и, если применимо, существующего коэффициента заполнения при отсутствии фрагментации.|  
|sample_size_with_current_compression_setting (КБ)|**bigint**|Размер образца с текущими настройками сжатия. К этим настройкам относится любая фрагментация.|  
|sample_size_with_requested_compression_setting (КБ)|**bigint**|Размер образца, созданного с использованием запрошенных настроек сжатия, и, если применимо, существующего коэффициента заполнения при отсутствии фрагментации.|  
  
## <a name="remarks"></a>Замечания  
 Чтобы оценить экономию от сжатия таблицы или секции на уровне строк или страниц, используется процедура sp_estimate_data_compression_savings. Например, если средний размер строки можно уменьшить на 40%, то размер самого объекта также можно потенциально уменьшить на 40%. Но выигрыша можно не получить, поскольку экономия места зависит от коэффициента заполнения и размера строки. Например, если длина строки, составляющая 8 000 байт, уменьшается на 40%, то на странице данных все равно помещается только одна строка. При этом экономия отсутствует.  
  
 Если результаты выполнения хранимой процедуры sp_estimate_data_compression_saving показывают, что размер таблицы будет увеличиваться, это означает, что в таблице используется почти полная точность типов данных, а небольшой объем затрат, необходимый для использования сжатого формата, — больше, чем экономия места от самого сжатия. В этом редком случае сжатие включать не следует.  
  
 Если для таблицы разрешено сжатие, использование процедуры sp_estimate_data_compression_savings позволяет оценить средний размер строки распакованной таблицы.  
  
 Во время этой операции для таблицы необходима блокировка (IS). Если блокировку (IS) получить невозможно, процедура блокируется. Таблица просматривается с уровнем изоляции read committed.  
  
 Если запрошенные настройки сжатия совпадают с текущими, хранимая процедура возвращает ожидаемый размер без фрагментации данных с текущим коэффициентом заполнения.  
  
 Если индекс или идентификатор секции не существует, результат не возвращается.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение SELECT на таблицу.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Эта процедура не применяется к таблицам columnstore, поэтому для нее не подходят параметры сжатия данных COLUMNSTORE и COLUMNSTORE_ARCHIVE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере оценивается размер таблицы `Production.WorkOrderRouting` в случае сжатия `ROW`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Компонент Database Engine хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Реализация сжатия Юникода](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
