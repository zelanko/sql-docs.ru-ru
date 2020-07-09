---
title: DBCC SHOWCONTIG (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC_SHOWCONTIG_TSQL
- DBCC SHOWCONTIG
- SHOWCONTIG
- SHOWCONTIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying defragmentation information
- DBCC SHOWCONTIG statement
- defragmenting indexes
- leaf level defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
ms.assetid: 1df2123a-1197-4fff-91a3-25e3d8848aaa
author: pmasl
ms.author: umajay
ms.openlocfilehash: 3e177015f1d17ff28fe702a4c5998f97999b66ec
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882034"
---
# <a name="dbcc-showcontig-transact-sql"></a>DBCC SHOWCONTIG (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Отображает сведения о фрагментации данных и индексов указанной таблицы или представления.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого функцию [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DBCC SHOWCONTIG   
[ (   
    { table_name | table_id | view_name | view_id }   
    [ , index_name | index_id ]   
) ]   
    [ WITH   
        {   
         [ , [ ALL_INDEXES ] ]   
         [ , [ TABLERESULTS ] ]   
         [ , [ FAST ] ]  
         [ , [ ALL_LEVELS ] ]   
         [ NO_INFOMSGS ]  
         }  
    ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *table_name* | *table_id* | *view_name* | *view_id*  
 Таблица или представление, для которых проверяются сведения о фрагментации. Если этот аргумент не указан, проверяются все таблицы и индексированные представления из текущей базы данных. Для получения идентификатора таблицы или представления используется функция [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md).  
  
 *index_name* | *index_id*  
 Индекс, для которого проверяются сведения о фрагментации. Если этот аргумент не задан, инструкция обрабатывает базовый индекс указанной таблицы или представления. Для получения идентификатора индекса используется представление каталога [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 WITH  
 Задает параметры типа возвращаемых инструкцией DBCC сведений.  
  
 FAST  
 Определяет, выполнять ли быстрый просмотр индекса с выводом минимального количества сведений. При быстром просмотре не считываются страницы индекса конечного уровня или уровня данных.  
  
 ALL_INDEXES  
 Отображает результаты для всех индексов заданных таблиц и представлений, даже если указан конкретный индекс.  
  
 TABLERESULTS  
 Отображает результаты в виде набора строк с дополнительными сведениями.  
  
 ALL_LEVELS  
 Поддерживается только для обратной совместимости. Даже если указан параметр ALL_LEVELS, обрабатывается только конечный уровень индекса или уровень данных таблицы.  
  
 NO_INFOMSGS  
 Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="result-sets"></a>Результирующие наборы  
В следующей таблице описаны сведения в результирующем наборе.
  
|Статистика|Описание|  
|---|---|
|**Pages Scanned**|Количество страниц в таблице или индексе.|  
|**Extents Scanned**|Количество экстентов в таблице или индексе.|  
|**Extent Switches**|Количество раз, когда инструкция DBCC в процессе обхода страниц таблицы или индекса переходила с одного экстента на другой.|  
|**Средн. Pages per Extent**|Количество страниц на экстент в цепочке страниц.|  
|**Scan Density [Best Count: Actual Count]**|Процентное отношение. Это отношение **Best Count** к **Actual Count**. Значение 100 указывает на отсутствие фрагментации; значение меньше 100 указывает на наличие фрагментации.<br /><br /> **Best Count** — это идеальное количество изменений экстентов в случае полной непрерывности. **Actual Count** — это реальное количество изменений экстентов.|  
|**Logical Scan Fragmentation**|Процент неупорядоченных страниц, определенный с помощью просмотра конечных страниц индекса. Это значение несущественно для куч. Неупорядоченной называется страница, для которой следующая физическая страница, выделенная для индекса, не является страницей, на которую ссылается указатель следующей страниц*ы* в текущей конечной странице.|  
|**Extent Scan Fragmentation**|Процент неупорядоченных экстентов при просмотре конечных страниц индекса. Это значение несущественно для куч. Неупорядоченным называется такой экстент, для которого экстент, содержащий текущую страницу индекса, не расположен физически непосредственно за экстентом, содержащим предыдущую страницу индекса.<br /><br /> Примечание. Это значение не имеет смысла, если индекс охватывает несколько файлов.|  
|**Средн. Bytes Free per Page**|Среднее количество свободных байтов на просмотренных страницах. Чем больше это число, тем меньше заполнены страницы. Предпочтительны более низкие показатели, если в индексе не будет большого количества случайных вставок. На этот показатель влияет также размер строк: большой размер строки может привести к его увеличению.|  
|**Средн. Page density (full)**|Средняя плотность страницы в процентах. Этот показатель учитывает размер строк. Поэтому он более точно отражает плотность заполнения страниц. Чем больше процентное отношение, тем лучше.|  
  
Если указаны параметры *table_id* и FAST, инструкция DBCC SHOWCONTIG возвращает в результирующем наборе только следующие столбцы.
-   **Pages Scanned**  
-   **Extent Switches**  
-   **Scan Density [Best Count:Actual Count]**  
-   **Extent Scan Fragmentation**  
-   **Logical Scan Fragmentation**  
  
Если указан параметр TABLERESULTS, инструкция DBCC SHOWCONTIG возвращает следующие столбцы дополнительно к девяти столбцам, описанным в предыдущей таблице.
  
|Статистика|Описание|  
|---|---|
|**Имени объекта**|Имя обработанной таблицы или представления.|  
|**ObjectId**|Идентификатор объекта.|  
|**IndexName**|Имя обработанного индекса. Для кучи это значение NULL.|  
|**IndexId**|Идентификатор индекса. Для кучи равен 0.|  
|**Level**|Уровень индекса. Уровень 0 представляет собой конечный уровень или уровень данных индекса.<br /><br /> Для кучи уровень равен 0.|  
|**Страницы**|Количество страниц, образующих данный уровень индекса или всю кучу.|  
|**Строки**|Количество записей данных или индексных записей на этом уровне индекса. Для кучи это число записей данных во всей куче.<br /><br /> Для кучи число записей, возвращаемых этой функцией, может не соответствовать числу строк, возвращаемых запросом SELECT COUNT(*) из кучи. Это происходит потому, что строка может содержать несколько записей. Например, при обновлении одна строка кучи может иметь указывающую запись и перенаправленную запись как результат операции обновления. Также большинство больших LOB-строк разбиты на различные записи в хранилище LOB_DATA.|  
|**MinimumRecordSize**|Минимальный размер записи на данном уровне индекса или во всей куче.|  
|**MaximumRecordSize**|Максимальный размер записи на данном уровне индекса или во всей куче.|  
|**AverageRecordSize**|Средний размер записи на данном уровне индекса или во всей куче.|  
|**ForwardedRecords**|Количество перенаправленных записей на данном уровне индекса или во всей куче.|  
|**Extents**|Количество экстентов на данном уровне индекса или во всей куче.|  
|**ExtentSwitches**|Количество раз, когда инструкция DBCC в процессе обхода страниц таблицы или индекса переходила с одного экстента на другой.|  
|**AverageFreeBytes**|Среднее количество свободных байтов на просмотренных страницах. Чем больше это число, тем меньше заполнены страницы. Предпочтительны более низкие показатели, если в индексе не будет большого количества случайных вставок. На этот показатель влияет также размер строк: большой размер строки может привести к его увеличению.|  
|**AveragePageDensity**|Средняя плотность страницы в процентах. Этот показатель учитывает размер строк. Поэтому он более точно отражает плотность заполнения страниц. Чем больше процентное отношение, тем лучше.|  
|**ScanDensity**|Процентное отношение. Это отношение значения **BestCount** к значению **ActualCount**. Значение 100 указывает на отсутствие фрагментации; значение меньше 100 указывает на наличие фрагментации.|  
|**BestCount**|Идеальное количество изменений экстентов в случае полной непрерывности.|  
|**ActualCount**|Реальное число изменений экстентов.|  
|**LogicalFragmentation**|Процент неупорядоченных страниц, определенный с помощью просмотра конечных страниц индекса. Это значение несущественно для куч. Неупорядоченной называется страница, для которой следующая физическая страница, выделенная для индекса, не является страницей, на которую ссылается указатель следующей страниц*ы* в текущей конечной странице.|  
|**ExtentFragmentation**|Процент неупорядоченных экстентов при просмотре конечных страниц индекса. Это значение несущественно для куч. Неупорядоченным называется такой экстент, для которого экстент, содержащий текущую страницу индекса, не расположен физически непосредственно за экстентом, содержащим предыдущую страницу индекса.<br /><br /> Примечание. Это значение не имеет смысла, если индекс охватывает несколько файлов.|  
  
Если указаны параметры WITH TABLERESULTS и FAST, результирующий набор ничем не отличается от набора, возвращаемого при указанном параметре WITH TABLERESULTS, за исключением того, что значения следующих столбцов равны NULL.

| Строки| Экстенты |
|---|---|
|**MinimumRecordSize**|**AverageFreeBytes**|  
|**MaximumRecordSize**|**AveragePageDensity**|  
|**AverageRecordSize**|**ExtentFragmentation**|  
|**ForwardedRecords**||  
  
## <a name="remarks"></a>Remarks  
Если задан аргумент *index_id*, инструкция DBCC SHOWCONTIG обходит цепочку страниц на конечном уровне заданного индекса. Если задан только аргумент *table_id* или же аргумент *index_id* равен 0, просматриваются страницы данных указанной таблицы. Для этой операции достаточно блокировки намерения (IS) таблицы. Таким способом можно выполнять все операции обновления и вставки, кроме операций, требующих монопольной (X) блокировки таблицы. Это позволяет достичь компромисса между скоростью выполнения без снижения параллелизма и числом возвращаемых статистических показателей. Однако, если команда используется только для оценки фрагментации, рекомендуется использовать параметр WITH FAST для оптимальной производительности. При быстром просмотре не считываются страницы индекса конечного уровня или уровня данных. Параметр WITH FAST неприменим к куче.
  
## <a name="restrictions"></a>Ограничения  
Инструкция DBCC SHOWCONTIG не отображает данные типов **ntext**, **text** и **image**. Это связано с тем, что текстовые индексы, в которых хранятся текстовые и графические данные, больше не существуют.
  
Кроме того, инструкция DBCC SHOWCONTIG не поддерживает некоторые новые возможности. Пример:
-   Если заданная таблица или индекс секционированы, инструкция DBCC SHOWCONTIG отображает только первую секцию заданной таблицы или индекса.  
-   Инструкция DBCC SHOWCONTIG не отображает сведения о хранении переполнения строки и других новых внестроковых типов данных, таких как **nvarchar(max)** , **varchar(max)** , **varbinary(max)** и **xml**.  
-   Пространственные индексы не поддерживаются инструкцией DBCC SHOWCONTIG.  
  
Полностью поддерживает все новые возможности динамического административного представления [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).
  
## <a name="table-fragmentation"></a>Фрагментация таблицы  
Инструкция DBCC SHOWCONTIG определяет, является ли таблица сильно фрагментированной. Фрагментация таблицы происходит в процессе изменения данных этой таблицы (инструкциями INSERT, UPDATE и DELETE). Так как эти изменения распределяются неравномерно между всеми строками таблицы, заполнение каждой страницы со временем может меняться. Для запросов, сканирующих часть или всю таблицу, такая фрагментация может привести к считыванию дополнительных страниц. Это затрудняет параллельный просмотр данных.
  
Если индекс сильно фрагментирован, для снижения фрагментации можно применить следующее.
-   Удалить и повторно создать кластеризованный индекс.  
     При повторном создании кластеризованного индекса данные реорганизуются, и страницы данных заполняются полностью. Уровень заполнения можно настроить с помощью параметра FILLFACTOR инструкции CREATE INDEX. К недостаткам этого метода относятся атомарный характер операции и переход индекса в режим вне сети во время цикла удаления или повторного создания. Если создание индекса прервано, он не создается заново.  
-   Повторно упорядочить страницы индекса конечного уровня в логическом порядке.  
     Повторно упорядочить страницы индекса конечного уровня в логическом порядке можно с помощью инструкции ALTER INDEX...REORGANIZE. Так как эта операция производится в режиме в сети, в процессе выполнения инструкции индекс остается доступным. Кроме того, операция может быть прервана без потери выполненной работы. Недостаток этого метода — эффективность реорганизации данных с его помощью ниже, чем при удалении и повторном создании кластеризованного индекса.  
-   Перестроить индекс.  
     Перестроить индекс можно с помощью инструкции ALTER INDEX с параметром REBUILD. Дополнительные сведения см. в разделе [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md).  
  
Показатель **Avg. Bytes free per page** и **Avg. Page density (full)** в результирующем наборе указывает на заполнение страниц индекса. Показатель **Avg. Bytes free per page** должен быть низким, а показатель **Avg. Page density (full)** — высоким для индекса с небольшим количеством случайных вставок. При удалении и повторном создании индекса с параметром FILLFACTOR показатели могут улучшиться. Кроме того, инструкция ALTER INDEX с параметром REORGANIZE позволяет сжать индекс, принимая во внимание его фактор заполнения FILLFACTOR, что также улучшит показатели.
  
> [!NOTE]  
>  В индексе с множеством случайных вставок и очень заполненными страницами возрастет количество разделений страниц. Это приводит к увеличению фрагментации.  
  
Уровень фрагментации индекса можно определить одним из следующих способов.
-   Сравнением значений **Extent Switches** и **Extents Scanned**.  
     Значение **Extent Switches** должно быть как можно ближе к значению **Extents Scanned**. Это отношение вычисляется как значение показателя **Scan Density**. Это значение должно быть как можно выше, и его можно улучшить, снизив уровень фрагментации индекса.  
  
    > [!NOTE]  
    >  Данный метод не работает в том случае, если индекс охватывает несколько файлов.  
  
-   Путем анализа значений **Logical Scan Fragmentation** и **Extent Scan Fragmentation**.  
     Значения **Logical Scan Fragmentation** и, в меньшей степени, значения **Extent Scan Fragmentation** являются наилучшими показателями уровня фрагментации таблицы. Оба значения должны быть как можно ближе к нулю, хотя значение от 0 до 10 процентов также приемлемо.  
  
    > [!NOTE]  
    >  Значение **Extent Scan Fragmentation** будет высоким, если индекс охватывает несколько файлов. Для снижения этих значений необходимо снизить уровень фрагментации индекса.  
  
## <a name="permissions"></a>Разрешения  
Пользователь должен быть либо владельцем таблицы, либо членом предопределенной роли сервера **sysadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_ddladmin**.
  
## <a name="examples"></a>Примеры  
### <a name="a-displaying-fragmentation-information-for-a-table"></a>A. Отображение сведений о фрагментации таблицы  
В следующем примере отображаются сведения о фрагментации таблицы `Employee`.
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG ('HumanResources.Employee');  
GO  
```  
  
### <a name="b-using-object_id-to-obtain-the-table-id-and-sysindexes-to-obtain-the-index-id"></a>Б. Использование функции OBJECT_ID для получения идентификатора таблицы и представления sys.indexes для получения идентификатора индекса  
В следующем примере функция `OBJECT_ID` и представление каталога `sys.indexes` используются для получения идентификаторов таблицы и индекса для индекса `AK_Product_Name` таблицы `Production.Product` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @id int, @indid int  
SET @id = OBJECT_ID('Production.Product')  
SELECT @indid = index_id   
FROM sys.indexes  
WHERE object_id = @id   
   AND name = 'AK_Product_Name'  
DBCC SHOWCONTIG (@id, @indid);  
GO  
```  
  
### <a name="c-displaying-an-abbreviated-result-set-for-a-table"></a>В. Отображение сокращенного результирующего набора для таблицы  
Следующий пример возвращает сокращенный результирующий набор для таблицы `Product` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG ('Production.Product', 1) WITH FAST;  
GO  
```  
  
### <a name="d-displaying-the-full-result-set-for-every-index-on-every-table-in-a-database"></a>Г. Отображение полного результирующего набора по каждому индексу каждой таблицы базы данных  
Следующий пример возвращает полный табличный результирующий набор по каждому индексу каждой таблицы в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG WITH TABLERESULTS, ALL_INDEXES;  
GO  
```  
  
### <a name="e-using-dbcc-showcontig-and-dbcc-indexdefrag-to-defragment-the-indexes-in-a-database"></a>Д. Использование DBCC SHOWCONTIG и DBCC INDEXDEFRAG для дефрагментации индексов в базе данных  
В следующем примере показан простой способ дефрагментации всех индексов базы данных, фрагментированной сверх определенного порога.
  
```sql
/*Perform a 'USE <database name>' to select the database in which to run the script.*/  
-- Declare variables  
SET NOCOUNT ON;  
DECLARE @tablename varchar(255);  
DECLARE @execstr   varchar(400);  
DECLARE @objectid  int;  
DECLARE @indexid   int;  
DECLARE @frag      decimal;  
DECLARE @maxfrag   decimal;  
  
-- Decide on the maximum fragmentation to allow for.  
SELECT @maxfrag = 30.0;  
  
-- Declare a cursor.  
DECLARE tables CURSOR FOR  
   SELECT TABLE_SCHEMA + '.' + TABLE_NAME  
   FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_TYPE = 'BASE TABLE';  
  
-- Create the table.  
CREATE TABLE #fraglist (  
   ObjectName char(255),  
   ObjectId int,  
   IndexName char(255),  
   IndexId int,  
   Lvl int,  
   CountPages int,  
   CountRows int,  
   MinRecSize int,  
   MaxRecSize int,  
   AvgRecSize int,  
   ForRecCount int,  
   Extents int,  
   ExtentSwitches int,  
   AvgFreeBytes int,  
   AvgPageDensity int,  
   ScanDensity decimal,  
   BestCount int,  
   ActualCount int,  
   LogicalFrag decimal,  
   ExtentFrag decimal);  
  
-- Open the cursor.  
OPEN tables;  
  
-- Loop through all the tables in the database.  
FETCH NEXT  
   FROM tables  
   INTO @tablename;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
-- Do the showcontig of all indexes of the table  
   INSERT INTO #fraglist   
   EXEC ('DBCC SHOWCONTIG (''' + @tablename + ''')   
      WITH FAST, TABLERESULTS, ALL_INDEXES, NO_INFOMSGS');  
   FETCH NEXT  
      FROM tables  
      INTO @tablename;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE tables;  
DEALLOCATE tables;  
  
-- Declare the cursor for the list of indexes to be defragged.  
DECLARE indexes CURSOR FOR  
   SELECT ObjectName, ObjectId, IndexId, LogicalFrag  
   FROM #fraglist  
   WHERE LogicalFrag >= @maxfrag  
      AND INDEXPROPERTY (ObjectId, IndexName, 'IndexDepth') > 0;  
  
-- Open the cursor.  
OPEN indexes;  
  
-- Loop through the indexes.  
FETCH NEXT  
   FROM indexes  
   INTO @tablename, @objectid, @indexid, @frag;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   PRINT 'Executing DBCC INDEXDEFRAG (0, ' + RTRIM(@tablename) + ',  
      ' + RTRIM(@indexid) + ') - fragmentation currently '  
       + RTRIM(CONVERT(varchar(15),@frag)) + '%';  
   SELECT @execstr = 'DBCC INDEXDEFRAG (0, ' + RTRIM(@objectid) + ',  
       ' + RTRIM(@indexid) + ')';  
   EXEC (@execstr);  
  
   FETCH NEXT  
      FROM indexes  
      INTO @tablename, @objectid, @indexid, @frag;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE indexes;  
DEALLOCATE indexes;  
  
-- Delete the temporary table.  
DROP TABLE #fraglist;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[OBJECT_ID (Transact-SQL)](../../t-sql/functions/object-id-transact-sql.md)  
[sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)
  
  

