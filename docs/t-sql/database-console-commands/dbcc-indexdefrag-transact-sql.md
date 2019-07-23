---
title: DBCC INDEXDEFRAG (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- INDEXDEFRAG
- DBCC INDEXDEFRAG
- DBCC_INDEXDEFRAG_TSQL
- INDEXDEFRAG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- defragmenting indexes
- DBCC INDEXDEFRAG statement
- leaf level defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
ms.assetid: 3c7df676-4843-44d0-8c1c-a9ab7e593b70
author: pmasl
ms.author: umajay
ms.openlocfilehash: 7372051d8dfb23430f834ca159125822c6892956
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116532"
---
# <a name="dbcc-indexdefrag-transact-sql"></a>DBCC INDEXDEFRAG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Дефрагментирует индексы указанной таблицы или представления.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого инструкцию [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md).  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC INDEXDEFRAG  
(  
    { database_name | database_id | 0 }   
    , { table_name | table_id | view_name | view_id }   
    [ , { index_name | index_id } [ , { partition_number | 0 } ] ]  
)  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* | *database_id* | 0  
 База данных, содержащая индекс для дефрагментации. Если указано значение 0, используется текущая база данных. Имена баз данных должны соответствовать правилам [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 *table_name* | *table_id* | *view_name* | *view_id*  
 Таблица или представление, содержащие индекс для дефрагментации. Имена таблиц и представлений должны соответствовать требованиям, предъявляемым к идентификаторам.  
  
 *index_name* | *index_id*  
 Имя или идентификатор индекса, подлежащего дефрагментации. Если этот аргумент не указан, дефрагментируются все индексы заданной таблицы или представления. Имена индексов должны соответствовать правилам для идентификаторов.  
  
 *partition_number* | 0  
 Номер секции индекса, которую следует дефрагментировать. Если этот аргумент не указан или равен 0, дефрагментируются все секции заданного индекса.  
  
 WITH NO_INFOMSGS  
 Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC INDEXDEFRAG дефрагментирует конечный уровень индекса, приводя физический порядок страниц в соответствие логическому порядку конечных узлов слева направо, что повышает эффективность сканирования индекса.
  
> [!NOTE]  
>  При выполнении инструкции DBCC INDEXDEFRAG дефрагментация индекса осуществляется последовательно. Это означает, что операции над одним индексом выполняются в одном потоке без параллелизма. Операции над несколькими индексами, относящиеся к одной инструкции DBCC INDEXDEFRAG, выполняются над одним индексом за раз.  
  
Кроме того, инструкция DBCC INDEXDEFRAG сжимает страницы индекса с учетом коэффициента заполнения, указанного при создании индекса. Любые пустые страницы при этом удаляются. Дополнительные сведения см. в статье [Указание коэффициента заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).
  
Если индекс охватывает более одного файла, инструкция DBCC INDEXDEFRAG дефрагментирует по одному файлу за раз. Страницы не перемещаются между файлами.
  
Инструкция DBCC INDEXDEFRAG сообщает процент выполнения дефрагментации каждые пять минут. Дефрагментацию можно остановить в любой момент, при этом вся выполненная работа сохраняется.
  
В отличие от инструкции DBCC DBREINDEX и операций создания индексов вообще, инструкция DBCC INDEXDEFRAG выполняется в режиме в сети. Она не удерживает блокировки длительное время. Таким образом, она не блокирует выполнение запросов или обновлений. Так как время дефрагментации зависит от степени фрагментации, сравнительно нефрагментированный индекс иногда можно дефрагментировать быстрее, чем создать новый индекс. На дефрагментацию сильно фрагментированного индекса может уйти гораздо больше времени, чем на его создание заново.
  
Процесс дефрагментации всегда полностью регистрируется в журнале независимо от модели восстановления баз данных. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md). Дефрагментация сильно фрагментированного индекса может привести к записи большего объема данных, чем создание индекса с полной регистрацией в журнале. Однако дефрагментация выполняется как ряд кратких транзакций, поэтому она не требует большого журнала, если часто создаются резервные копии журнала или если применяется простая (SIMPLE) модель восстановления.
  
## <a name="restrictions"></a>Ограничения  
Инструкция DBCC INDEXDEFRAG перемещает конечные страницы индекса в произвольном порядке. Таким образом, если содержимое индекса чередуется на диске с содержимым других индексов, выполнение инструкции DBCC INDEXDEFRAG для этого индекса не приведет к расположению всех конечных страниц индекса в последовательном порядке. Чтобы улучшить кластеризацию страниц, создайте индекс заново.
Инструкция DBCC INDEXDEFRAG не может быть использована для дефрагментации следующих индексов.
-   Отключенный индекс.  
-   Индекс с отключенной блокировкой страниц.  
-   Пространственный индекс.  
  
Эта инструкция не поддерживает системные таблицы.
  
## <a name="result-sets"></a>Результирующие наборы  
Если в инструкции DBCC INDEXDEFRAG указан индекс (но не указан аргумент WITH NO_INFOMSGS), она возвращает следующий результирующий набор (значения могут быть иными):
  
```sql
Pages Scanned Pages Moved Pages Removed  
------------- ----------- -------------  
359           346         8  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Вызывающий должен быть владельцем таблицы, членом предопределенной роли сервера **sysadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_ddladmin**.
  
## <a name="examples"></a>Примеры  
### <a name="a-using-dbcc-indexdefrag-to-defragment-an-index"></a>A. Использование DBCC INDEXDEFRAG для дефрагментации индекса  
Приведенный ниже код дефрагментирует все секции индекса `PK_Product_ProductID` таблицы `Production.Product` в базе данных `AdventureWorks`.
  
```sql  
DBCC INDEXDEFRAG (AdventureWorks2012, 'Production.Product', PK_Product_ProductID);  
GO  
```  
  
### <a name="b-using-dbcc-showcontig-and-dbcc-indexdefrag-to-defragment-the-indexes-in-a-database"></a>Б. Использование DBCC SHOWCONTIG и DBCC INDEXDEFRAG для дефрагментации индексов в базе данных  
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
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)
  
  

