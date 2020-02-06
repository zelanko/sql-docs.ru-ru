---
title: DBCC DBREINDEX (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC DBREINDEX
- DBREINDEX_TSQL
- DBREINDEX
- DBCC_DBREINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- index rebuilding [SQL Server]
- rebuilding indexes
- dynamic index rebuilding [SQL Server]
- DBCC DBREINDEX statement
ms.assetid: 6e929d09-ccb5-4855-a6af-b616022bc8f6
author: pmasl
ms.author: umajay
ms.openlocfilehash: 5aa089ac3c8de549e0c2ec33fd413c9cafba24dd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68101989"
---
# <a name="dbcc-dbreindex-transact-sql"></a>DBCC DBREINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Перестраивает один или более индексов для таблицы в указанной базе данных.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого инструкцию [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md).  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
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
 *table_name*  
 Имя таблицы, содержащей указанный индекс или индексы для перестроения. Имена таблиц должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md) *.*  
  
 *index_name*  
 Имя перестраиваемого индекса. Имена индексов должны соответствовать правилам для идентификаторов. Если аргумент *index_name* задан, также должен быть указан аргумент *table_name*. Если аргумент *index_name* не задан или имеет значение " ", перестраиваются все индексы таблицы.  
  
 *fillfactor*  
 Процентная доля пространства на каждой странице индексов при создании или перестроении индекса. Аргумент *fillfactor* заменяет коэффициент заполнения, указанный при создании индекса, и становится новым значением по умолчанию для данного индекса и любых других некластеризованных индексов, перестраиваемых из-за перестроения кластеризованного индекса.  
 Если значение аргумента *fillfactor* равно 0, в инструкции DBCC DBREINDEX используется последнее указанное значение коэффициента заполнения для индекса. Это значение хранится в представлении каталога **sys.indexes**.   
 Если аргумент *fillfactor* задан, также должны быть указаны аргументы *table_name* и *index_name*. Если аргумент *fillfactor* не задан, используется установленный по умолчанию коэффициент заполнения 100. Дополнительные сведения см. в статье [Указание коэффициента заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 WITH NO_INFOMSGS  
 Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="remarks"></a>Remarks  
Инструкция DBCC DBREINDEX выполняет перестроение индекса для таблицы или всех индексов, определенных для таблицы. При разрешенном динамическом перестроении индекса индексы с ограничениями PRIMARY KEY или UNIQUE можно перестраивать без необходимости удаления и повторного создания этих ограничений. Это значит, что индекс может быть перестроен без необходимости знания структуры таблицы или ее ограничений. Потребность в этом может возникнуть после массового копирования данных в таблицу.

Инструкция DBCC DBREINDEX позволяет перестроить все индексы таблицы с помощью одной инструкции. Это проще, чем кодирование множества инструкций DROP INDEX и CREATE INDEX. Так как работа выполняется одной инструкцией, инструкция DBCC DBREINDEX автоматически становится атомарной, в то время как отдельные инструкции DROP INDEX и CREATE INDEX необходимо включить в транзакцию, чтобы они стали атомарными. Кроме того, инструкция DBCC DBREINDEX дает большее преимущество в оптимизации по сравнению с отдельными инструкциями DROP INDEX и CREATE INDEX.

В отличие от инструкций DBCC INDEXDEFRAG или от ALTER INDEX с параметром REORGANIZE, DBCC DBREINDEX является операцией вне сети. Если перестраивается некластеризованный индекс, для запрашиваемой таблицы в течение операции удерживается совместная блокировка. Это предотвращает изменения в таблице. Если перестраивается кластеризованный индекс, удерживается монопольная блокировка таблицы. Это предотвращает какой-либо доступ к таблице, делая ее вне сети. Для оперативного перестроения индекса используется инструкция ALTER INDEX REBUILD с параметром ONLINE; она также используется для управления степенью параллелизма в течение операции перестроения индекса.

Дополнительные сведения о выборе метода перестроения или реорганизации индекса см. в статье [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).
  
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
Вызывающий должен быть владельцем таблицы, членом предопределенной роли сервера **sysadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_ddladmin**.
  
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
  
## <a name="see-also"></a>См. также:  
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)  
  
  

