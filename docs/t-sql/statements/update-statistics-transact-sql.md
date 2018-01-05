---
title: "Инструкции UPDATE STATISTICS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE STATISTICS
- UPDATE_STATISTICS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- updating statistics
- query optimization statistics [SQL Server], updating
- UPDATE STATISTICS statement
- statistical information [SQL Server], updating
ms.assetid: 919158f2-38d0-4f68-82ab-e1633bd0d308
caps.latest.revision: "74"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c69949773ff1dae533c98d087780a2f4b436b62
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="update-statistics-transact-sql"></a>UPDATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Обновляет статистику оптимизации запросов для таблицы или индексированного представления. По умолчанию оптимизатор запросов обновляет статистику по мере необходимости для усовершенствования плана запроса. в некоторых случаях можно повысить производительность запросов с помощью инструкции UPDATE STATISTICS или хранимой процедуры [sp_updatestats](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md) обновление статистики чаще, чем это происходит по умолчанию.  
  
 Обновление статистики гарантирует, что запросы будут компилироваться с актуальной статистикой. Однако обновление статистики вызывает перекомпиляцию запросов. Рекомендуется не обновлять статистику слишком часто, поскольку необходимо найти баланс между выигрышем в производительности за счет усовершенствованных планов запросов и потерей времени на перекомпиляцию запросов. Критерии выбора компромиссного решения зависят от приложения. UPDATE STATISTICS может использовать базу данных tempdb для сортировки образцов строк для построения статистики.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
UPDATE STATISTICS table_or_indexed_view_name   
    [   
        {   
            { index_or_statistics__name }  
          | ( { index_or_statistics_name } [ ,...n ] )   
                }  
    ]   
    [    WITH   
        [  
            FULLSCAN   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | SAMPLE number { PERCENT | ROWS }   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | RESAMPLE   
              [ ON PARTITIONS ( { <partition_number> | <range> } [, …n] ) ]  
            | <update_stats_stream_option> [ ,...n ]  
        ]   
        [ [ , ] [ ALL | COLUMNS | INDEX ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ] 
        [ [ , ] MAXDOP = max_degree_of_parallelism ] 
    ] ;  
  
<update_stats_stream_option> ::=  
    [ STATS_STREAM = stats_stream ]  
    [ ROWCOUNT = numeric_constant ]  
    [ PAGECOUNT = numeric_contant ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
UPDATE STATISTICS schema_name . ] table_name   
    [ ( { statistics_name | index_name } ) ]  
    [ WITH   
       {  
              FULLSCAN   
            | SAMPLE number PERCENT   
            | RESAMPLE   
        }  
    ]  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_or_indexed_view_name*  
 — Это имя таблицы или индексированного представления, содержащего объект статистики.  
  
 *index_or_statistics_name*  
 Имя индекса, для которого обновляется статистика, или имя обновляемой статистики. Если *index_or_statistics_name* не указан, оптимизатор запросов обновляет всю статистику для таблицы или индексированного представления. Сюда входит статистика, созданная инструкцией CREATE STATISTICS, статистика по отдельным столбцам, созданная при включенном параметре AUTO_CREATE_STATISTICS, и статистика, созданная для индексов.  
  
 Дополнительные сведения о параметре AUTO_CREATE_STATISTICS см. в разделе [параметры ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Чтобы просмотреть все индексы для таблицы или представления, можно использовать [sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
 FULLSCAN  
 Вычисляет статистику путем просмотра всех строк в таблице или индексированном представлении. FULLSCAN и SAMPLE 100 PERCENT имеют одинаковые результаты. FULLSCAN не может быть использован с параметром SAMPLE.  
  
 Образец *номер* {% | СТРОКИ}  
 Указывает приблизительное процентное соотношение или число строк в таблице или индексированном представлении для оптимизатора запросов, которые используются при обновлении статистики. Для параметра PERCENT *номер* может быть от 0 до 100, а для СТРОК, *номер* может составлять от 0 до общее число строк. Фактическое процентное соотношение или число строк, отбираемых оптимизатором запросов, может не совпадать с заданным значением. Например, оптимизатор запросов просматривает все строки на странице данных.  
  
 Команда SAMPLE полезна в особых случаях, в которых план запроса на основе выборки по умолчанию не является оптимальным. В большинстве случаев нет необходимости использовать команду SAMPLE, так как оптимизатор запросов делает выборку и определяет размер статистически значимой выборки по умолчанию, что требуется для создания высококачественных планов запроса. 
 
Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], выборки данных для построения статистики выполняется в параллельном режиме, при использовании уровня совместимости 130, чтобы повысить производительность сбор статистики. Оптимизатор запросов будет использовать статистику образца всякий раз, когда размер таблицы превышает определенный порог. 
   
 Параметр SAMPLE нельзя использовать вместе с параметром FULLSCAN. Если не указана ни одна из команд SAMPLE или FULLSCAN, оптимизатор запросов использует выбранные данные и вычисляет размер выборки по умолчанию.  
  
 Не рекомендуется указывать значения 0 PERCENT и 0 ROWS. Если для PERCENT или ROWS указано значение 0, объект статистики будет обновлен без статистических данных.  
  
 В большинстве рабочих нагрузок полная проверка не требуется и выборки по умолчанию является достаточным.  
Тем не менее некоторых рабочих нагрузок, которые чувствительны к совершенно разными распределения данных может потребоваться увеличение выборке, либо полное сканирование.  
Дополнительные сведения см. в разделе [блоге CSS SQL укрупнения служб](http://blogs.msdn.com/b/psssql/archive/2010/07/09/sampling-can-produce-less-accurate-statistics-if-the-data-is-not-evenly-distributed.aspx).  
  
 RESAMPLE  
 Обновить каждый объект статистики, используя последнее значение частоты выборки.  
  
 Использование RESAMPLE может вызвать просмотр полной таблицы. Например, статистика для индексов использует для частоты выборки просмотр полной таблицы. Если не указан ни один из параметров выборки (SAMPLE, FULLSCAN, RESAMPLE), оптимизатор запросов выполняет выборку данных и вычисляет размер выборки по умолчанию.  

PERSIST_SAMPLE_PERCENT = {ON | {OFF}  
Когда **ON**, статистики будут сохранять Процент выборки набора для последующих обновлений, которые явно не указан процент выборки. Когда **OFF**, Процент выборки статистика будет сброшен для выборки по умолчанию при последующих обновлениях, которые явно не указан процент выборки. Значение по умолчанию — **OFF**. 
 
 > [!NOTE]
 > Если параметр AUTO_UPDATE_STATISTICS выполняется, использует материализованные выборки процентное значение, если он доступен или использовать Процент выборки по умолчанию, если это не так.
 > ОБРАБОТАЙТЕ этот параметр не влияет на поведение.
 
 > [!TIP] 
 > [Инструкция DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) и [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md) предоставлять сохраненного примерное процентное значение для выбранной статистики.
 
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4) через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU1).  
 
 В СЕКЦИИ ({ \<partition_number > | \<диапазона >} [,... n]) ] Принудительно статистик конечного уровня, посвященных секциям в предложении ON PARTITIONS пересчитываются, и затем объединяются для создания глобальных статистик. WITH RESAMPLE обязательно, потому что статистики секции, построенные с различной частотой выборки, нельзя объединить.  
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ALL | COLUMNS | INDEX  
 Обновить всю существующую статистику, созданную по одному или нескольким столбцам, или статистику, созданную для индексов. Если не указан ни один параметр, инструкция UPDATE STATISTICS обновляет всю статистику для таблицы или индексированного представления.  
  
 NORECOMPUTE  
 Отключить параметр автоматического обновления статистики AUTO_UPDATE_STATISTICS для указанной статистики. Если указан этот параметр, оптимизатор запросов завершает текущее обновление статистики и отключает обновление в будущем.  
  
 Повторное включение параметра AUTO_UPDATE_STATISTICS, снова запустите инструкцию UPDATE STATISTICS без параметра NORECOMPUTE или запускаться **sp_autostats**.  
  
> [!WARNING]  
>  Использование этого параметра может привести к созданию неоптимальных планов запросов. Рекомендуется ограничить использование этого параметра, причем использовать его надлежит только опытным системным администраторам.  
  
 Дополнительные сведения о параметре auto_statistics_update см. в разделе [параметры ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 INCREMENTAL = { ON | OFF }  
 Когда **ON**, статистики повторно создаются согласно статистики секции. Когда **OFF**, дерево статистик удаляется и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторно вычисляет статистики. Значение по умолчанию — **OFF**.  
  
 Если статистики по секциям не поддерживаются, возвращается ошибка. Добавочные статистики не поддерживаются для следующих типов статистических данных.  
  
-   Статистики, созданные с индексами, не выровненными по секциям для базовой таблицы.  
-   Статистики, созданные в доступных для чтения базах данных-получателях AlwaysOn.  
-   Статистики, созданные в базах данных, доступных только для чтения.  
-   Статистики, созданные по фильтрованным индексам.  
-   Статистика, созданная по представлениям.  
-   Статистики, созданные по внутренним таблицам.  
-   Статистики, созданные с пространственными индексами или XML-индексами.  
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]

MAXDOP = *max_degree_of_parallelism*  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3).  
  
 Переопределяет **максимальная степень параллелизма** параметр конфигурации в течение операции статистики. Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). MAXDOP можно использовать для ограничения числа процессоров, используемых при параллельном выполнении планов. Максимальное число процессоров — 64.  
  
 *max_degree_of_parallelism* может быть:  
  
 1  
 Подавляет формирование параллельных планов.  
  
 \>1  
 Ограничивает максимальное количество процессоров, используемых в операциях параллельных статистики с заданным или меньшим числом в зависимости от текущей рабочей нагрузки системы.  
  
 0 (по умолчанию)  
 В зависимости от текущей рабочей нагрузки системы использует реальное или меньшее число процессоров.  
  
 \<update_stats_stream_option >[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  

## <a name="remarks"></a>Remarks  
  
## <a name="when-to-use-update-statistics"></a>Условия использования инструкции UPDATE STATISTICS  
 Дополнительные сведения об использовании инструкции UPDATE STATISTICS см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  

## <a name="limitations-and-restrictions"></a>Ограничения  
* Обновление статистики во внешних таблицах не поддерживается. Для обновления статистики в external table, drop и повторного создания статистики.  
* Параметр MAXDOP несовместим с параметрами STATS_STREAM, количество СТРОК и PAGECOUNT.

## <a name="updating-all-statistics-with-spupdatestats"></a>Обновление всей статистики с помощью процедуры sp_updatestats  
 Сведения об обновлении статистики по всем определяемым пользователем таблицам и внутренним таблицам в базе данных см. в описании хранимой процедуры [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md). Например, следующая команда вызывает процедуру sp_updatestats для обновления всей статистики для базы данных.  
  
```sql  
EXEC sp_updatestats;  
```  
  
## <a name="determining-the-last-statistics-update"></a>Определение времени последнего обновления статистики  
 Чтобы определить время последнего обновления статистики, используйте функцию [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) .  
  
## <a name="pdw--sql-data-warehouse"></a>PDW или хранилище данных SQL  
 Следующий синтаксис не поддерживается в PDW или хранилище данных SQL  
  
```sql  
update statistics t1 (a,b);   
```  
  
```sql  
update statistics t1 (a) with sample 10 rows;  
```  
  
```sql  
update statistics t1 (a) with NORECOMPUTE;  
```  
  
```sql  
update statistics t1 (a) with INCREMENTAL=ON;  
```  
  
```sql  
update statistics t1 (a) with stats_stream = 0x01;  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER для таблицы или представления.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-update-all-statistics-on-a-table"></a>A. Обновление всей статистики для таблицы  
 В следующем примере обновляется статистика для всех индексов на `SalesOrderDetail` таблицы.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail;  
GO  
```  
  
### <a name="b-update-the-statistics-for-an-index"></a>Б. Обновление статистики для индекса  
 В следующем примере обновляется статистика для индекса `AK_SalesOrderDetail_rowguid` в таблице `SalesOrderDetail`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;  
GO  
```  
  
### <a name="c-update-statistics-by-using-50-percent-sampling"></a>В. Обновление статистики с применением 50-процентной выборки  
 В следующем примере создается, а затем обновляется статистика для столбцов `Name` и `ProductNumber` в таблице `Product`.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE STATISTICS Products  
    ON Production.Product ([Name], ProductNumber)  
    WITH SAMPLE 50 PERCENT  
-- Time passes. The UPDATE STATISTICS statement is then executed.  
UPDATE STATISTICS Production.Product(Products)   
    WITH SAMPLE 50 PERCENT;  
```  
  
### <a name="d-update-statistics-by-using-fullscan-and-norecompute"></a>Г. Обновление статистики с использованием параметров FULLSCAN и NORECOMPUTE  
 В следующем примере обновляется статистика `Products` в таблице `Product`, принудительно запускается полный просмотр всех строк таблицы `Product` и отключается автоматическое обновление статистики `Products`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Production.Product(Products)  
    WITH FULLSCAN, NORECOMPUTE;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-update-statistics-on-a-table"></a>Д. Обновление статистики для таблицы  
 В следующем примере обновляется `CustomerStats1` статистики по `Customer` таблицы.  
  
```sql  
UPDATE STATISTICS Customer ( CustomerStats1 );  
```  
  
### <a name="f-update-statistics-by-using-a-full-scan"></a>Е. Обновить статистику с помощью полной проверки  
 В следующем примере обновляется `CustomerStats1` статистику, на основании сканирования всех строк в `Customer` таблицы.  
  
```sql  
UPDATE STATISTICS Customer (CustomerStats1) WITH FULLSCAN;  
```  
  
### <a name="g-update-all-statistics-on-a-table"></a>Ж. Обновление всей статистики для таблицы  
 Следующий пример обновляет всю статистику на `Customer` таблицы.  
  
```sql  
UPDATE STATISTICS Customer;  
```  
  
## <a name="see-also"></a>См. также:  
 [Статистика](../../relational-databases/statistics/statistics.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_updatestats (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [STATS_DATE &#40; Transact-SQL &#41;](../../t-sql/functions/stats-date-transact-sql.md)  
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md) [sys.dm_db_stats_histogram &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  



