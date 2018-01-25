---
title: "Инструкция DBCC DBREINDEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC DBREINDEX
- DBREINDEX_TSQL
- DBREINDEX
- DBCC_DBREINDEX_TSQL
dev_langs: TSQL
helpviewer_keywords:
- index rebuilding [SQL Server]
- rebuilding indexes
- dynamic index rebuilding [SQL Server]
- DBCC DBREINDEX statement
ms.assetid: 6e929d09-ccb5-4855-a6af-b616022bc8f6
caps.latest.revision: "52"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 991c16eea9a651270ca299e72cafbc822465a9b3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dbreindex-transact-sql"></a>DBCC DBREINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Перестраивает один или несколько индексов для таблицы в указанной базе данных.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Используйте [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) вместо него.  
  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC DBREINDEX   
(   
    table_name   
    [ , index_name [ , fillfactor ] ]  
)  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_таблицы*  
 Имя таблицы, содержащей указанный индекс или индексы для перестроения. Имена таблиц должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md)*.*  
  
 *index_name*  
 Имя перестраиваемого индекса. Имена индексов должны соответствовать правилам для идентификаторов. Если *index_name* указано, *table_name* должен быть указан. Если *index_name* не задано или равно "«, перестраиваются все индексы для таблицы.  
  
 *fillfactor*  
 Процентная доля пространства на каждой странице индексов при создании или перестроении индекса. *значение коэффициента заполнения* заменяет коэффициент заполнения при создании индекса, становится новое значение по умолчанию для данного индекса и любых других некластеризованных индексов, перестраиваемых из-за перестроения кластеризованного индекса.  
 Когда *fillfactor* равно 0, инструкция DBCC DBREINDEX используется значение коэффициента заполнения для индекса последнего заданного. Это значение хранится в **sys.indexes** представления каталога.   
 Если *fillfactor* указано, *table_name* и *index_name* должен быть указан. Если *fillfactor* не указан, используется по умолчанию коэффициент заполнения, 100,. Дополнительные сведения см. в статье [Указание коэффициента заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 WITH NO_INFOMSGS  
 Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC DBREINDEX выполняет перестроение индекса для таблицы или всех индексов, определенных для таблицы. При разрешенном динамическом перестроении индекса индексы с ограничениями PRIMARY KEY или UNIQUE можно перестраивать без необходимости удаления и повторного создания этих ограничений. Это значит, что индекс может быть перестроен без необходимости знания структуры таблицы или ее ограничений. Потребность в этом может возникнуть после массового копирования данных в таблицу.

Инструкция DBCC DBREINDEX позволяет перестроить все индексы таблицы с помощью одной инструкции. Это проще, чем кодирование множества инструкций DROP INDEX и CREATE INDEX. Так как работа выполняется одной инструкцией, инструкция DBCC DBREINDEX автоматически становится атомарной, в то время как отдельные инструкции DROP INDEX и CREATE INDEX необходимо включить в транзакцию, чтобы они стали атомарными. Кроме того, инструкция DBCC DBREINDEX дает большее преимущество в оптимизации по сравнению с отдельными инструкциями DROP INDEX и CREATE INDEX.

В отличие от инструкций DBCC INDEXDEFRAG или от ALTER INDEX с параметром REORGANIZE, DBCC DBREINDEX является операцией вне сети. Если перестраивается некластеризованный индекс, для запрашиваемой таблицы в течение операции удерживается совместная блокировка. Это предотвращает изменения в таблице. Если перестраивается кластеризованный индекс, удерживается монопольная блокировка таблицы. Это предотвращает какой-либо доступ к таблице, делая ее вне сети. Для оперативного перестроения индекса используется инструкция ALTER INDEX REBUILD с параметром ONLINE; она также используется для управления степенью параллелизма в течение операции перестроения индекса.

Дополнительные сведения о выборе метода перестроения или реорганизации индекса см. в разделе [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md) .
  
## <a name="restrictions"></a>Ограничения  
Использование инструкции DBCC DBREINDEX не поддерживается для следующих объектов:
-   Системные таблицы  
-   Пространственные индексы  
-   индексы columnstore, оптимизированные для памяти xVelocity  
  
## <a name="result-sets"></a>Результирующие наборы  
Даже если не задан NO_INFOMSGS (имя таблицы задавать необходимо), инструкция DBCC DBREINDEX возвращает:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Вызывающий объект должен быть владельцем таблицы или быть членом **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных или **db_ddladmin** предопределенной роли базы данных.
  
## <a name="examples"></a>Примеры  
### <a name="a-rebuilding-an-index"></a>A. Перестроение индекса  
В следующем примере перестраивается кластеризованный индекс `Employee_EmployeeID` с коэффициентом заполнения `80` для таблицы `Employee` базы данных `AdventureWorks`.
  
```sql  
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', PK_Employee_BusinessEntityID,80);  
GO  
```  
  
### <a name="b-rebuilding-all-indexes"></a>Б. Перестроение всех индексов  
В следующем примере перестраиваются все индексы для таблицы `Employee` базы данных `AdventureWorks` при значении коэффициента заполнения `70`.
  
```sql
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', ' ', 70);  
GO  
```  
  
## <a name="see-also"></a>См. также  
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
[sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)  
  
  

