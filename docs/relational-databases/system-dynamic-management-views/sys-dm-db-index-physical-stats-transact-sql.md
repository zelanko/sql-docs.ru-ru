---
title: sys.dm_db_index_physical_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_index_physical_stats
- sys.dm_db_index_physical_stats_TSQL
- sys.dm_db_index_physical_stats
- dm_db_index_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_physical_stats dynamic management function
- fragmentation [SQL Server]
ms.assetid: d294dd8e-82d5-4628-aa2d-e57702230613
caps.latest.revision: 95
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1853bdbf62701cfbaa5302615eac61684089ac5a
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34468080"
---
# <a name="sysdmdbindexphysicalstats-transact-sql"></a>sys.dm_db_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о размере и фрагментации данных и индексов указанной таблицы или представления в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для индекса возвращается одна строка для каждого уровня сбалансированного дерева в каждой секции. Для кучи возвращается одна строка для единицы распределения IN_ROW_DATA каждой секции. Для данных больших объектов (LOB) возвращается одна строка для единицы распределения LOB_DATA каждой секции. Если в таблице существуют данные с переполнением строки, то возвращается одна строка для единицы распределения ROW_OVERFLOW_DATA в каждой секции. Не возвращает информацию об индексах columnstore с оптимизированной памятью xVelocity.  
  
> [!IMPORTANT]
> При выполнении запроса **sys.dm_db_index_physical_stats** на экземпляре сервера, на котором размещается Always On [вторичная реплика](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md), могут возникнуть критическое препятствие REDO. Это связано с тем, что данное динамическое административное представление получает блокировку (IS) в указанной пользовательской таблице либо в представлении, которые могут блокировать запросы посредством потока REDO для монопольной блокировки (X) этой пользовательской таблицы или представления.  
  
 **sys.dm_db_index_physical_stats** не возвращает сведения об индексах оптимизированных для памяти. Сведения об использовании индекса, оптимизированного для памяти см. в разделе [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_db_index_physical_stats (   
    { database_id | NULL | 0 | DEFAULT }  
  , { object_id | NULL | 0 | DEFAULT }  
  , { index_id | NULL | 0 | -1 | DEFAULT }  
  , { partition_number | NULL | 0 | DEFAULT }  
  , { mode | NULL | DEFAULT }  
)  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_id* | ЗНАЧЕНИЕ NULL | 0 | ПО УМОЛЧАНИЮ  
 Идентификатор базы данных. *database_id* — **smallint**. Допустимыми входными значениями являются идентификатор базы данных, NULL, 0 или DEFAULT. Значение по умолчанию равно 0. В данном контексте значения NULL, 0 и DEFAULT эквивалентны.  
  
 Укажите значение NULL, чтобы вернуть сведения для всех баз данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если указать значение NULL для *database_id*, необходимо также указать значение NULL для *object_id*, *index_id*, и *partition_number*.  
  
 Встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md) можно указать. Если функция DB_ID используется без указания имени базы данных, то уровень совместимости текущей базы данных должен быть равен 90 или выше.  
  
 *object_id* | ЗНАЧЕНИЕ NULL | 0 | ПО УМОЛЧАНИЮ  
 Идентификатор объекта таблицы или представления, имеющего индекс. *object_id* имеет тип **int**.  
  
 Допустимыми входными значениями являются идентификатор таблицы, NULL, 0 или DEFAULT. Значение по умолчанию равно 0. В данном контексте значения NULL, 0 и DEFAULT эквивалентны. По состоянию на [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], допустимые входные значения также включать имя очереди service broker или имя внутренней таблицы очереди. Если применяются параметры по умолчанию (т. е. все объекты, всех индексов и т. д), сведения о фрагментации для всех очередей, включаются в результирующий набор.  
  
 Укажите значение NULL, чтобы вернуть данные для всех таблиц и представлений в указанной базе данных. Если указать значение NULL для *object_id*, необходимо также указать значение NULL для *index_id* и *partition_number*.  
  
 *index_id* | 0 | ЗНАЧЕНИЕ NULL | -1 | ПО УМОЛЧАНИЮ  
 Идентификатор индекса. *index_id* — **int**. Допустимыми входными значениями являются идентификатор индекса, 0, если *object_id* является кучей, NULL, -1 или DEFAULT. Значение по умолчанию — -1. Имеет значение NULL, значение -1 и по умолчанию, равные значения в этом контексте.  
  
 Укажите значение NULL, чтобы вернуть данные для всех индексов базовой таблицы или представления. Если указать значение NULL для *index_id*, необходимо также указать значение NULL для *partition_number*.  
  
 *partition_number* | ЗНАЧЕНИЕ NULL | 0 | ПО УМОЛЧАНИЮ  
 Номер секции в объекте. *partition_number* — **int**. Допустимыми входными значениями являются *partion_number* индекса или кучи, NULL, 0 или DEFAULT. Значение по умолчанию равно 0. В данном контексте значения NULL, 0 и DEFAULT эквивалентны.  
  
 Чтобы получить сведения обо всех секциях объекта, укажите значение NULL.  
  
 *partition_number* начинается с 1. Несекционированный индекс или куча имеет *partition_number* равным 1.  
  
 *режим* | ЗНАЧЕНИЕ NULL | ПО УМОЛЧАНИЮ  
 Имя режима. *режим* задает уровень просмотра, который используется для получения статистики. *режим* — **sysname**. Допустимыми входными данными являются значения DEFAULT, NULL, LIMITED, SAMPLED и DETAILED. Значение по умолчанию (NULL) соответствует значению LIMITED.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|Идентификатор базы данных таблицы или представления.|  
|object_id|**int**|Идентификатор объекта таблицы или представления, для которых создан индекс.|  
|index_id|**int**|Идентификатор индекса.<br /><br /> 0 = куча.|  
|partition_number|**int**|	Номер секции объекта, значения начинаются с 1; для таблицы, представления или индекса.<br /><br /> 1 = несекционированный индекс или куча.|  
|index_type_desc|**nvarchar(60)**|Описание типа индекса:<br /><br /> HEAP<br /><br /> CLUSTERED INDEX<br /><br /> NONCLUSTERED INDEX<br /><br /> PRIMARY XML INDEX<br /><br /> SPATIAL INDEX<br /><br /> XML INDEX<br /><br /> СОПОСТАВЛЕНИЕ ИНДЕКСА COLUMNSTORE (внутренний)<br /><br /> Индекс DELETEBUFFER COLUMNSTORE (внутренний)<br /><br /> Индекс DELETEBITMAP COLUMNSTORE (внутренний)|  
|hobt_id|**bigint**|Куча или сбалансированное дерево идентификатор индекса или секции.<br /><br /> Кроме возвращения hobt_id пользовательские индексы, также возвращает hobt_id индексы внутренней columnstore.|  
|alloc_unit_type_desc|**nvarchar(60)**|Описание типа единицы распределения:<br /><br /> IN_ROW_DATA<br /><br /> LOB_DATA<br /><br /> ROW_OVERFLOW_DATA<br /><br /> Единица распределения LOB_DATA содержит данные, которые хранятся в столбцах типа **текст**, **ntext**, **изображения**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, и **xml**. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).<br /><br /> Единица распределения ROW_OVERFLOW_DATA содержит данные, которые хранятся в столбцах типа **varchar(n)**, **nvarchar(n)**, **varbinary(n)**, и **sql_ Variant** которые выведены за пределы строки.|  
|index_depth|**tinyint**|Количество уровней индекса.<br /><br /> 1 = куча или единица распределения LOB_DATA или ROW_OVERFLOW_DATA.|  
|index_level|**tinyint**|Текущий уровень индекса.<br /><br /> 0 для конечного уровня индекса, для кучи и единиц распределения LOB_DATA или ROW_OVERFLOW_DATA.<br /><br /> Значения больше 0 соответствуют неконечным уровням индекса. *index_level* будет самым высоким на корневом уровне индекса.<br /><br /> Доступны только в неконечные уровни индекса обрабатываются, если *режим* = DETAILED.|  
|avg_fragmentation_in_percent|**float**|Логическая фрагментация для индексов или фрагментация экстентов для куч в единице распределения IN_ROW_DATA.<br /><br /> Значение измеряется в процентах и учитывает несколько файлов. Определения логической фрагментации и фрагментации экстентов см. в разделе «Замечания».<br /><br /> 0 для единиц распределения LOB_DATA и ROW_OVERFLOW_DATA.<br /><br /> Значение NULL для куч, если указан *режим* = SAMPLED.|  
|fragment_count|**bigint**|Количество фрагментов на конечном уровне единицы распределения IN_ROW_DATA. Дополнительные сведения о фрагментах см. в разделе «Замечания».<br /><br /> NULL для неконечных уровней индекса и единиц распределения LOB_DATA или ROW_OVERFLOW_DATA.<br /><br /> Значение NULL для куч, если указан *режим* = SAMPLED.|  
|avg_fragment_size_in_pages|**float**|Среднее количество страниц в одном фрагменте на конечном уровне единицы распределения IN_ROW_DATA.<br /><br /> NULL для неконечных уровней индекса и единиц распределения LOB_DATA или ROW_OVERFLOW_DATA.<br /><br /> Значение NULL для куч, если указан *режим* = SAMPLED.|  
|page_count|**bigint**|Общее количество страниц индекса или данных.<br /><br /> Для индекса — общее количество страниц индекса на текущем уровне сбалансированного дерева в единице распределения IN_ROW_DATA.<br /><br /> Для кучи — общее количество страниц данных в единице распределения IN_ROW_DATA.<br /><br /> Для единиц распределения LOB_DATA или ROW_OVERFLOW_DATA — общее количество страниц в единице распределения.|  
|avg_page_space_used_in_percent|**float**|Средний процент доступного места для хранения данных, используемого всеми страницами.<br /><br /> Для индекса усреднение применяется к текущему уровню сбалансированного дерева в единице распределения IN_ROW_DATA.<br /><br /> Для кучи — среднее значение для всех страниц данных в единице распределения IN_ROW_DATA.<br /><br /> Для единиц распределения LOB_DATA или ROW_OVERFLOW_DATA — среднее значение для всех страниц в единице распределения.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|record_count|**bigint**|Общее количество записей.<br /><br /> Для индекса общее количество записей применяется к текущему уровню сбалансированного дерева в единице распределения IN_ROW_DATA.<br /><br /> Для кучи — общее количество записей в единице распределения IN_ROW_DATA.<br /><br /> **Примечание:** для кучи число записей, возвращаемых этой функцией может не соответствовать число строк, возвращаемых, запустив ВЫБЕРИТЕ СЧЕТЧИК (\*) для кучи. Это происходит потому, что строка может содержать несколько записей. Например, при обновлении одна строка кучи может иметь указывающую запись и перенаправленную запись как результат операции обновления. Также большинство больших LOB-строк разбиты на различные записи в хранилище LOB_DATA.<br /><br /> Для единиц распределения LOB_DATA или ROW_OVERFLOW_DATA — общее количество записей во всей единице распределения.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|ghost_record_count|**bigint**|Количество фантомных записей в единице распределения, готовых к удалению задачей очистки фантомных записей.<br /><br /> 0 для неконечных уровней индекса в единице распределения IN_ROW_DATA.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|version_ghost_record_count|**bigint**|Количество фантомных записей, сохраняемых в единице распределения необработанной транзакцией изоляции моментального снимка.<br /><br /> 0 для неконечных уровней индекса в единице распределения IN_ROW_DATA.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|min_record_size_in_bytes|**int**|Минимальный размер записи в байтах.<br /><br /> Для индекса минимальный размер записи применяется к текущему уровню сбалансированного дерева в единице распределения IN_ROW_DATA.<br /><br /> Для кучи — минимальный размер записи в единице распределения IN_ROW_DATA.<br /><br /> Для единиц распределения LOB_DATA или ROW_OVERFLOW_DATA — минимальный размер записи во всей единице распределения.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|max_record_size_in_bytes|**int**|Максимальный размер записи в байтах.<br /><br /> Для индекса максимальный размер записи применяется к текущему уровню сбалансированного дерева в единице распределения IN_ROW_DATA.<br /><br /> Для кучи — максимальный размер записи в единице распределения IN_ROW_DATA.<br /><br /> Для единиц распределения LOB_DATA или ROW_OVERFLOW_DATA — максимальный размер записи во всей единице распределения.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|avg_record_size_in_bytes|**float**|Средний размер записи в байтах.<br /><br /> Для индекса средний размер записи применяется к текущему уровню сбалансированного дерева в единице распределения IN_ROW_DATA.<br /><br /> Для кучи — средний размер записи в единице распределения IN_ROW_DATA.<br /><br /> Для единиц распределения LOB_DATA или ROW_OVERFLOW_DATA — средний размер записи во всей единице распределения.<br /><br /> Значение NULL, если *режим* = LIMITED.|  
|forwarded_record_count|**bigint**|Количество записей в куче, содержащих указатели на данные в других местах. (Такое состояние возникает во время обновления, когда не хватает места для сохранения новой строки в исходном расположении.)<br /><br /> NULL для любой единицы распределения, отличающейся от единиц распределения IN_ROW_DATA для кучи.<br /><br /> Значение NULL для куч, если указан *режим* = LIMITED.|  
|compressed_page_count|**bigint**|Количество сжатых страниц.<br /><br /> Вновь выделенные для куч страницы не сжаты с использованием сжатия PAGE. Куча — это СТРАНИЦА, сжимаемая при наступлении двух особых условий: при массовом импорте данных или при перестройке кучи. Типичные операции DML, которые вызывают выделение страниц, не связаны со сжатием PAGE. Перестройте кучу, если значение compressed_page_count увеличивается сверх желательного порога.<br /><br /> Для таблиц с кластеризованным индексом значение compressed_page_count указывает эффективность сжатия страниц.|  
|hobt_id|bigint|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Применительно к индексам columnstore только это идентификатор набора строк, который отслеживает внутренние columnstore данные для секции. Наборы строк не хранимые как для кучи данных или двоичного дерева. Они имеют одинаковые Идентификаторы индекса как родительский индекс columnstore. Дополнительные сведения см. в разделе [sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md).<br /><br /> Значение NULL, если|  
|column_store_delete_buffer_state|tinyint|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = OPEN;<br /><br /> 2 = СТОК<br /><br /> 3 = ЗАПИСЬ НА ДИСК<br /><br /> 4 = СНЯТИЯ С УЧЕТА<br /><br /> 5 = ГОТОВНОСТЬ|  
|column_store_delete_buff_state_desc||**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> NOT_APPLICABLE — родительский индекс не является индексом columnstore.<br /><br /> OPEN — методов Deleter и сканеры используйте его.<br /><br /> СТОК — методов Deleter расходуя, но сканеры по-прежнему использовать.<br /><br /> ОЧИСТКА — буфер закрыт и строк в буфере, записываются в точечном рисунке delete.<br /><br /> Снятия с УЧЕТА — строк в буфере закрытых delete были записаны в точечном рисунке delete, но буфер не был усечен, поскольку сканеры используют ее. Новый сканеры нет необходимости использовать приходят буфера, поскольку достаточно открыть буфера.<br /><br /> ГОТОВ – это буфера удаления готов к использованию.|  
  
## <a name="remarks"></a>Примечания  
 Функция динамического управления sys.dm_db_index_physical_stats заменяет инструкцию DBCC SHOWCONTIG.  
  
## <a name="scanning-modes"></a>Режимы просмотра  
 Режим, в котором выполняется функция, определяет уровень просмотра для получения статистических данных, используемых функцией. *режим* указывается как LIMITED, SAMPLED или DETAILED. Эта функция проходит цепочки страниц в поисках единиц распределения, составляющих заданные секции таблицы или индекса. sys.dm_db_index_physical_stats требует только намерением совмещаемого доступа (IS) блокировки таблицы типа, независимо от режима, в котором она выполняется.  
  
 Режим LIMITED является самым быстрым, в нем производится наименьшее число просмотров страниц. Для индекса просматриваются только страницы родительского уровня в сбалансированном дереве (то есть страницы, расположенные выше конечного уровня). Для кучи просматриваются только связанные PFS- и IAM-страницы. Страницы данных в куче просматриваются в режиме LIMITED.  
  
 В режиме LIMITED счетчик compressed_page_count имеет значение NULL, поскольку компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] просматривает только неконечные страницы сбалансированного дерева, а также IAM- и PFS-страницы кучи. Используйте режим SAMPLED для получения оценочного значения счетчика compressed_page_count и режим DETAILED, чтобы получить фактическое значение счетчика compressed_page_count. В режиме SAMPLED возвращается статистика на основе 1-процентной выборки всех страниц в индексе или куче. Результаты в режиме SAMPLED следует рассматривать как приблизительные. Если в индексе или куче менее 10 000 страниц, вместо режима SAMPLED используется режим DETAILED.  
  
 В режиме DETAILED проводится просмотр всех страниц и возвращается вся статистика.  
  
 Режимы характеризуются снижением скорости, начиная с LIMITED и заканчивая DETAILED, т. к. в каждом последующем режиме этой последовательности выполняется все больший объем работы. Для быстрого измерения уровня фрагментации таблицы или индекса используйте режим LIMITED. Это самый быстрый режим, и для неконечных уровней индекса в единице распределения IN_ROW_DATA строки в нем не возвращаются.  
  
## <a name="using-system-functions-to-specify-parameter-values"></a>Использование системных функций для указания значений параметров  
 Можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] функции [DB_ID](../../t-sql/functions/db-id-transact-sql.md) и [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md) для указания значения для *database_id* и *object_id* параметры. Однако передавая значения, которые не допустимы для этих функций, можно получить неожиданные результаты. Например, если имя базы данных или объекта не могут быть найдены из-за того, что объект или база данных не существуют или соответствующее имя указано неверно, обе функции возвращают NULL. Функция sys.dm_db_index_physical_stats интерпретирует NULL как значение шаблона, задающее все базы данных или все объекты.  
  
 Кроме того, функция OBJECT_ID, выполненная перед функцией sys.dm_db_index_physical_stats вызывается и поэтому вычисляется в контексте текущей базы данных, не указана в *database_id*. Это поведение может привести к тому, что функция OBJECT_ID возвратит значение NULL или, если имя объекта существует в контексте как текущей, так и указанной базы данных, возвратит сообщение об ошибке. В следующих примерах демонстрируются эти неожиданные результаты.  
  
```  
USE master;  
GO  
-- In this example, OBJECT_ID is evaluated in the context of the master database.   
-- Because Person.Address does not exist in master, the function returns NULL.  
-- When NULL is specified as an object_id, all objects in the database are returned.  
-- The same results are returned when an object that is not valid is specified.  
SELECT * FROM sys.dm_db_index_physical_stats  
    (DB_ID(N'AdventureWorks'), OBJECT_ID(N'Person.Address'), NULL, NULL , 'DETAILED');  
GO  
-- This example demonstrates the results of specifying a valid object name  
-- that exists in both the current database context and  
-- in the database specified in the database_id parameter of the   
-- sys.dm_db_index_physical_stats function.  
-- An error is returned because the ID value returned by OBJECT_ID does not  
-- match the ID value of the object in the specified database.  
CREATE DATABASE Test;  
GO  
USE Test;  
GO  
CREATE SCHEMA Person;  
GO  
CREATE Table Person.Address(c1 int);  
GO  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_index_physical_stats  
    (DB_ID(N'Test'), OBJECT_ID(N'Person.Address'), NULL, NULL , 'DETAILED');  
GO  
-- Clean up temporary database.  
DROP DATABASE Test;  
GO  
```  
  
### <a name="best-practice"></a>Рекомендации  
 Всегда следует проверять, что функции DB_ID и OBJECT_ID возвращают допустимый идентификатор. Например, при использовании OBJECT_ID укажите трехкомпонентного имени например `OBJECT_ID(N'AdventureWorks2012.Person.Address')`, или проверяйте значение, возвращаемое этими функциями, прежде чем использовать их в функции sys.dm_db_index_physical_stats. Примеры А и Б демонстрируют безопасный способ указания базы данных и идентификаторов объектов.  
  
## <a name="detecting-fragmentation"></a>Выявление фрагментации  
 Фрагментация возникает в процессе изменений данных (инструкциями INSERT, UPDATE и DELETE), выполняемых на таблице и, следовательно, в индексах, определенных для таблицы. Так как эти изменения обычно не распределяются равномерно по строкам таблицы и индекса, заполненность каждой страницы со временем может меняться. Для запросов, выполняющих просмотр части или всех индексов таблицы, этот вид фрагментации может приводить к чтению дополнительных страниц. Это затрудняет параллельный просмотр данных.  
  
 Уровень фрагментации индекса или кучи показан в столбце avg_fragmentation_in_percent. Для куч это значение соответствует фрагментации экстентов. Для индексов это значение соответствует логической фрагментации. В отличие от инструкции DBCC SHOWCONTIG, алгоритмы вычисления фрагментации в обоих случаях учитывают место для хранения нескольких файлов и поэтому являются точными.  
  
 **Логическая фрагментация**  
  
 Это процент неупорядоченных страниц конечного уровня индекса. Неупорядоченной называется страница, для которой следующая физическая страница, выделенная для индекса, не является страницей, на которую ссылается указатель следующей страниц*ы* в текущей конечной странице.  
  
 **Фрагментация экстентов**  
  
 Это процент неупорядоченных экстентов на конечном уровне кучи. Неупорядоченным называется такой экстент, для которого экстент, содержащий текущую страницу кучи, не расположен физически непосредственно за кластером, содержащим предыдущую страницу.  
  
 Для обеспечения наибольшей производительности значение аргумента avg_fragmentation_in_percent должно быть как можно более близким к нулю. Но могут быть приемлемыми значения от 0 до 10 процентов. Для снижения этих значений могут использоваться любые методы снижения фрагментации, такие как перестройка, реорганизация или повторное создание. Дополнительные сведения об анализе степени фрагментации индекса см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
## <a name="reducing-fragmentation-in-an-index"></a>Снижение фрагментации в индексе  
 Если индекс становится фрагментирован настолько, что это влияет на производительность запросов, для снижения фрагментации есть три возможности.  
  
-   Удаление и повторное создание кластеризованного индекса.  
  
     Повторное создание кластеризованного индекса перераспределяет данные и приводит к полному заполнению страниц данных. Уровень заполнения можно настроить с помощью параметра FILLFACTOR инструкции CREATE INDEX. Недостатком этого метода является то, что в цикле удаления и повторного создания индекс находится в автономном режиме, а также то, что эта операция является атомарной. Если создание индекса прервано, он не создается заново. Дополнительные сведения см. в разделе [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md).  
  
-   Использование инструкции ALTER INDEX REORGANIZE, заменившей DBCC INDEXDEFRAG, для переупорядочения страниц индекса конечного уровня в логическом порядке. Так как эта операция выполняется в режиме «в сети», во время выполнения инструкции индекс доступен. Кроме того, операция может быть прервана без потери уже выполненной работы. Недостатком этого метода является то, что он не так хорошо выполняет реорганизацию данных, как операция перестроения индекса, и не обновляет статистику.  
  
-   Использование инструкции ALTER INDEX REBUILD, заменившей DBCC DBREINDEX, для перестроения индекса, как «в сети», так и в режиме «вне сети». Дополнительные сведения см. в статье [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md).  
  
 Фрагментация сама по себе не является достаточной причиной реорганизации или перестроения индекса. Основной эффект фрагментации заключается в том, что она замедляет упреждающее чтение во время просмотра индекса. В результате этого увеличивается время ответа. Если запрос к фрагментированным таблице или индексу не предусматривает просмотра, потому что в основном выполняются единичные уточняющие запросы, устранение фрагментации может не дать никакого эффекта. Дополнительные сведения см. в этой [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?linkid=31012).  
  
> [!NOTE]  
>  Выполнение инструкции DBCC SHRINKFILE или DBCC SHRINKDATABASE может вызвать фрагментацию, если индекс частично или полностью перемещается во время операции сжатия. Поэтому, если необходимо выполнить операцию сжатия, нужно выполнить ее до устранения фрагментации.  
  
## <a name="reducing-fragmentation-in-a-heap"></a>Снижение фрагментации в куче  
 Для снижения фрагментации экстентов кучи создайте кластеризованный индекс таблицы, а затем удалите его. Во время создания кластеризованного индекса данные перераспределяются. Также эта операция выполняется наиболее оптимальным способом, учитывая распределение свободного места, доступного базе данных. Когда затем кластеризованный индекс удаляется для повторного создания кучи, данные не перемещаются и их распределение остается оптимальным. Сведения о способах выполнения этих операций см. в разделе [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) и [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md).  
  
> [!CAUTION]  
>  При создании и удалении кластеризованного индекса таблицы дважды перестраиваются все ее некластеризованные индексы.  
  
## <a name="compacting-large-object-data"></a>Сжатие данных больших объектов  
 По умолчанию инструкция ALTER INDEX REORGANIZE делает более компактными страницы, содержащие данные больших объектов (LOB). Так как страницы LOB не освобождаются, когда становятся пустыми, сжатие этих данных может оптимизировать использование места на диске, если удаляются в больших объемах данные LOB или же столбцы LOB.  
  
 Изменение указанного кластеризованного индекса сжимает все столбцы LOB, которые содержатся в кластеризованном индексе. Изменение некластеризованного индекса сжимает все столбцы LOB, являющиеся неключевыми столбцами, включенными в индекс. При использовании в инструкции аргумента ALL реорганизуются все индексы, связанные с указанной таблицей или представлением. Кроме того, сжимаются все столбцы LOB, связанные с кластеризованным индексом, базовой таблицей или некластеризованным индексом с включенными столбцами.  
  
## <a name="evaluating-disk-space-use"></a>Оценка использования места на диске  
 Столбец avg_page_space_used_in_percent указывает заполненность страниц. Для достижения оптимального использования места на диске это значение должно быть близким к 100 процентам для индексов, где операции случайных вставок выполняются нечасто. Однако в индексе с множеством случайных вставок, имеющем очень заполненные страницы, будет расти число разбиений страниц. Это приводит к увеличению фрагментации. Поэтому для снижения числа разбиений страниц это значение должно быть меньше 100 процентов. Перестроение индекса с параметром FILLFACTOR позволяет изменять степень заполнения страницы для обеспечения соответствия индекса шаблону запроса. Дополнительные сведения о коэффициенте заполнения см. в разделе [укажите коэффициент заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md). Кроме того, инструкция ALTER INDEX REORGANIZE сжимает индекс, пытаясь заполнять страницы до последнего заданного значения аргумента FILLFACTOR. Благодаря этому увеличивается значение avg_space_used_in_percent. Обратите внимание, что инструкция ALTER INDEX REORGANIZE не может снизить степень заполнения страницы. Для этого необходимо выполнить перестроение индекса.  
  
## <a name="evaluating-index-fragments"></a>Оценка фрагментов индекса  
 Фрагмент состоит из физически последовательных конечных страниц в одном файле единицы распределения. Индекс состоит, по крайней мере, из одного фрагмента. Максимальное число фрагментов, которое может иметь индекс, равно числу страниц на конечном уровне индекса. Увеличение размера фрагментов означает, что для считывания того же количества страниц понадобится меньшее количество обращений к диску. Следовательно, чем больше значение avg_fragment_size_in_pages, тем выше производительность при просмотре диапазона. Значения avg_fragment_size_in_pages и avg_fragmentation_in_percent обратно пропорциональны друг другу. То есть перестройка или реорганизация индекса уменьшают степень фрагментации и увеличивают размер фрагментов.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Не возвращает данные для кластеризованных индексов columnstore.  
  
## <a name="permissions"></a>Разрешения  
 Необходимы следующие разрешения:  
  
-   разрешение CONTROL на указанный объект в базе данных;  
  
-   Разрешение VIEW DATABASE STATE для возврата сведений обо всех объектах в указанной базе данных, с помощью объекта подстановочный знак @*object_id*= NULL.  
  
-   Разрешение VIEW SERVER STATE для возврата сведений обо всех базах данных, используя шаблон базы данных @*database_id* = NULL.  
  
 Предоставление разрешения VIEW DATABASE STATE позволяет всем объектам в базе данных быть возвращаемыми, независимо от любых разрешений CONTROL, запрещенных для определенных объектов.  
  
 Запрет разрешения VIEW DATABASE STATE запрещает всем объектам в базе данных быть возвращаемыми, независимо от любых разрешений CONTROL, предоставленных на определенные объекты. Кроме того, если шаблон базы данных @*database_id*= указано значение NULL, эта база данных пропускается.  
  
 Дополнительные сведения см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-information-about-a-specified-table"></a>A. Возврат сведений об указанной таблице  
 В следующем примере возвращаются размер и статистика фрагментации для всех индексов и секций таблицы `Person.Address`. Для повышения производительности и ограничения возвращаемой статистики используется режим просмотра `'LIMITED'`. Для выполнения этого запроса необходимо по крайней мере разрешение CONTROL на таблицу `Person.Address`.  
  
```  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
  
IF @db_id IS NULL  
BEGIN;  
    PRINT N'Invalid database';  
END;  
ELSE IF @object_id IS NULL  
BEGIN;  
    PRINT N'Invalid object';  
END;  
ELSE  
BEGIN;  
    SELECT * FROM sys.dm_db_index_physical_stats(@db_id, @object_id, NULL, NULL , 'LIMITED');  
END;  
GO  
  
```  
  
### <a name="b-returning-information-about-a-heap"></a>Б. Возврат сведений о куче  
 В следующем примере возвращается вся статистика для кучи `dbo.DatabaseLog` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Поскольку таблица содержит данные типа LOB, возвращается строка для `LOB_DATA` единицы распределения, кроме строки, возвращаемой для `IN_ROW_ALLOCATION_UNIT` , хранящей страницы данных кучи. Для выполнения этого запроса необходимо по крайней мере разрешение CONTROL на таблицу `dbo.DatabaseLog`.  
  
```  
DECLARE @db_id SMALLINT;  
DECLARE @object_id INT;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.dbo.DatabaseLog');  
IF @object_id IS NULL   
BEGIN;  
    PRINT N'Invalid object';  
END;  
ELSE  
BEGIN;  
    SELECT * FROM sys.dm_db_index_physical_stats(@db_id, @object_id, 0, NULL , 'DETAILED');  
END;  
GO  
  
```  
  
### <a name="c-returning-information-for-all-databases"></a>В. Возврат сведений обо всех базах данных  
 В следующем примере возвращается вся статистика для всех таблиц и индексов экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для этого всем параметрам задается символ-шаблон `NULL`. Для выполнения этого запроса необходимо разрешение VIEW SERVER STATE.  
  
```  
SELECT * FROM sys.dm_db_index_physical_stats (NULL, NULL, NULL, NULL, NULL);  
GO  
  
```  
  
### <a name="d-using-sysdmdbindexphysicalstats-in-a-script-to-rebuild-or-reorganize-indexes"></a>Г. Использование представления sys.dm_db_index_physical_stats в скрипте для перестроения или реорганизации индексов  
 В следующем примере автоматически реорганизуются или перестраиваются все секции в базе данных со средней степенью фрагментации более 10 процентов. Для выполнения этого запроса необходимо разрешение VIEW DATABASE STATE. В данном примере в качестве первого параметра указывается `DB_ID` без определения имени базы данных. Если уровень совместимости текущей базы данных составляет 80 или ниже, будет сформирована ошибка. Чтобы исправить эту ошибку, замените вызов функции `DB_ID()` действительным именем базы данных. Дополнительные сведения об уровнях совместимости баз данных см. в разделе [уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
```  
-- Ensure a USE <databasename> statement has been executed first.  
SET NOCOUNT ON;  
DECLARE @objectid int;  
DECLARE @indexid int;  
DECLARE @partitioncount bigint;  
DECLARE @schemaname nvarchar(130);   
DECLARE @objectname nvarchar(130);   
DECLARE @indexname nvarchar(130);   
DECLARE @partitionnum bigint;  
DECLARE @partitions bigint;  
DECLARE @frag float;  
DECLARE @command nvarchar(4000);   
-- Conditionally select tables and indexes from the sys.dm_db_index_physical_stats function   
-- and convert object and index IDs to names.  
SELECT  
    object_id AS objectid,  
    index_id AS indexid,  
    partition_number AS partitionnum,  
    avg_fragmentation_in_percent AS frag  
INTO #work_to_do  
FROM sys.dm_db_index_physical_stats (DB_ID(), NULL, NULL , NULL, 'LIMITED')  
WHERE avg_fragmentation_in_percent > 10.0 AND index_id > 0;  
  
-- Declare the cursor for the list of partitions to be processed.  
DECLARE partitions CURSOR FOR SELECT * FROM #work_to_do;  
  
-- Open the cursor.  
OPEN partitions;  
  
-- Loop through the partitions.  
WHILE (1=1)  
    BEGIN;  
        FETCH NEXT  
           FROM partitions  
           INTO @objectid, @indexid, @partitionnum, @frag;  
        IF @@FETCH_STATUS < 0 BREAK;  
        SELECT @objectname = QUOTENAME(o.name), @schemaname = QUOTENAME(s.name)  
        FROM sys.objects AS o  
        JOIN sys.schemas as s ON s.schema_id = o.schema_id  
        WHERE o.object_id = @objectid;  
        SELECT @indexname = QUOTENAME(name)  
        FROM sys.indexes  
        WHERE  object_id = @objectid AND index_id = @indexid;  
        SELECT @partitioncount = count (*)  
        FROM sys.partitions  
        WHERE object_id = @objectid AND index_id = @indexid;  
  
-- 30 is an arbitrary decision point at which to switch between reorganizing and rebuilding.  
        IF @frag < 30.0  
            SET @command = N'ALTER INDEX ' + @indexname + N' ON ' + @schemaname + N'.' + @objectname + N' REORGANIZE';  
        IF @frag >= 30.0  
            SET @command = N'ALTER INDEX ' + @indexname + N' ON ' + @schemaname + N'.' + @objectname + N' REBUILD';  
        IF @partitioncount > 1  
            SET @command = @command + N' PARTITION=' + CAST(@partitionnum AS nvarchar(10));  
        EXEC (@command);  
        PRINT N'Executed: ' + @command;  
    END;  
  
-- Close and deallocate the cursor.  
CLOSE partitions;  
DEALLOCATE partitions;  
  
-- Drop the temporary table.  
DROP TABLE #work_to_do;  
GO  
  
```  
  
### <a name="e-using-sysdmdbindexphysicalstats-to-show-the-number-of-page-compressed-pages"></a>Д. Использование представления sys.dm_db_index_physical_stats для отображения числа страниц, подвергнутых сжатию на уровне страниц  
 В следующем примере демонстрируется отображение и сравнение общего числа страниц со страницами, подвергнутыми сжатию на уровне страниц и на уровне строк. Эти сведения могут быть использованы для определения полезности сжатия для индекса или таблицы.  
  
```  
SELECT o.name,  
    ips.partition_number,  
    ips.index_type_desc,  
    ips.record_count, ips.avg_record_size_in_bytes,  
    ips.min_record_size_in_bytes,  
    ips.max_record_size_in_bytes,  
    ips.page_count, ips.compressed_page_count  
FROM sys.dm_db_index_physical_stats ( DB_ID(), NULL, NULL, NULL, 'DETAILED') ips  
JOIN sys.objects o on o.object_id = ips.object_id  
ORDER BY record_count DESC;  
```  
  
### <a name="f-using-sysdmdbindexphysicalstats-in-sampled-mode"></a>Е. Использование sys.dm_db_index_physical_stats в режиме SAMPLED  
 В следующем примере показано, как в режиме SAMPLED возвращается примерное значение, отличающееся от результатов в режиме DETAILED.  
  
```  
CREATE TABLE t3 (col1 int PRIMARY KEY, col2 varchar(500)) WITH(DATA_COMPRESSION = PAGE);  
GO  
BEGIN TRAN  
DECLARE @idx int = 0;  
WHILE @idx < 1000000  
BEGIN  
    INSERT INTO t3 (col1, col2)   
    VALUES (@idx,   
    REPLICATE ('a', 100) + CAST (@idx as varchar(10)) + REPLICATE ('a', 380))  
    SET @idx = @idx + 1  
END  
COMMIT;  
GO  
SELECT page_count, compressed_page_count, forwarded_record_count, *   
FROM sys.dm_db_index_physical_stats (db_id(),   
    object_id ('t3'), null, null, 'SAMPLED');  
SELECT page_count, compressed_page_count, forwarded_record_count, *   
FROM sys.dm_db_index_physical_stats (db_id(),   
    object_id ('t3'), null, null, 'DETAILED');  
```  
  
### <a name="g-querying-service-broker-queues-for-index-fragmentation"></a>Ж. Запросы очередей компонента service broker для фрагментации индекса  
  
||  
|-|  
|**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 В следующих примерах показано, как создать запрос очередей server broker для фрагментации.  
  
```  
--Using queue internal table name   
select * from sys.dm_db_index_physical_stats (db_id(), object_id ('sys.queue_messages_549576996'), default, default, default)   
  
--Using queue name directly  
select * from sys.dm_db_index_physical_stats (db_id(), object_id ('ExpenseQueue'), default, default, default)  
  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)   
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  

