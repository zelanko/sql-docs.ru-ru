---
title: "RENAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/13/2016
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 0907cfd9-33a6-4fa6-91da-7d6679fee878
caps.latest.revision: 15
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d58470957ab58085ddd6a733cf30dbc77ce7439a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rename-transact-sql"></a>RENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Переименование таблицы, созданные пользователем, в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Переименовывает пользовательской таблицы или базы данных в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
> [!NOTE]  
>  Переименование базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssSDS](../../includes/sssds-md.md)] хранимая процедура [sp_renamedb &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-renamedb-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
-- Rename a table.  
RENAME OBJECT [ :: ]  [ [ database_name .  [schema_name ] ] . ] | [schema_name . ] ] table_name TO new_table_name  
[;]  
  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- Rename a table  
RENAME OBJECT [::] [ [ database_name . [ schema_name ] . ] | [ schema_name . ] ] table_name TO new_table_name  
[;]  
  
-- Rename a database  
RENAME DATABASE [::] database_name TO new_database_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 ПЕРЕИМЕНОВАТЬ ОБЪЕКТ [:]   
          [[*имя_базы_данных* . [ *schema_name* ]. ] | [ *schema_name* . []]*table_name* TO *new_table_name*  
 **ПРИМЕНЯЕТСЯ К:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Измените имя определяемой пользователем таблицей. Укажите таблицу для переименования с одно-, двух- или трехкомпонентное имя.    Укажите новую таблицу *new_table_name* виде однокомпонентного имени.  
  
 ПЕРЕИМЕНОВАНИЕ БАЗЫ ДАННЫХ [:]   
          [ *имя_базы_данных* TO *новое_имя_базы_данных*  
 **ОБЛАСТЬ ПРИМЕНЕНИЯ:**  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Измените имя пользовательской базы данных из *имя_базы_данных* для *новое_имя_базы_данных*.  Невозможно переименовать базу данных на любой из этих [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]зарезервированные имена баз данных:  
  
-   master  
  
-   model  
  
-   msdb  
  
-   tempdb  
  
-   pdwtempdb1  
  
-   pdwtempdb2  
  
-   : DWConfiguration  
  
-   DWDiagnostics  
  
-   DWQueue  
  
## <a name="permissions"></a>Permissions  
 Для выполнения этой команды требуется это разрешение:  
  
-   **ALTER** разрешение на таблицу  
   
  
## <a name="limitations-and-restrictions"></a>Ограничения  
  
### <a name="cannot-rename-an-external-table-indexes-or-views"></a>Не удается переименовать внешней таблицы, индексов или представления
Не удается переименовать внешней таблицы, индексов или представления. Вместо переименования можно удалить внешней таблицы, индекса или представления и затем создать его повторно с новым именем.

### <a name="cannot-rename-a-table-in-use"></a>Не удалось переименовать таблицу используется  
 Нельзя переименовать таблицы или базы данных во время использования. Переименование таблицы требуется монопольная блокировка таблицы. Если таблицы, может потребоваться Завершить сеансы на основе таблицы. Для завершения сеанса можно использовать команду KILL. Используйте инструкцию KILL осторожно, так как при завершении сеанса все незафиксированная работа будет выполнен откат. Сеансы в хранилище данных SQL добавляет префикс «SID». Необходимо включить это и номер сеанса при вызове команды KILL. Этот пример просматривает список активных или неактивных сеансов и затем завершает сеанс «SID1234».  
  
### <a name="views-are-not-updated"></a>Представления не обновляются.  
 При переименовании базы данных, все представления, которые используют имя бывшие базы данных станут недействительными. Это относится к представлениям внутри и вне базы данных. Например, при переименовании базы данных Sales представления, содержащий `SELECT * FROM Sales.dbo.table1` станут недействительными. Чтобы устранить эту проблему, можно избегать использования трехкомпонентные имена в представлениях или обновление представлений для ссылки на новое имя базы данных.  
  
 При переименовании таблицы, представления не обновляются для ссылки на новое имя таблицы. Каждое представление внутри или за пределами базы данных, который ссылается на имя таблицы бывшая станут недействительными. Чтобы устранить эту проблему, можно обновить каждое представление для ссылки на новое имя таблицы.  
  
## <a name="locking"></a>Блокировка  
 Переименование таблицы принимает совмещаемую блокировку для объекта базы данных, совмещаемую блокировку для объекта СХЕМЫ и монопольной блокировки на таблицу.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-rename-a-database"></a>A. Переименование базы данных  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] только    
  
 В этом примере переименовывает определяемую пользователем базу данных AdWorks в AdWorks2.  
  
```  
-- Rename the user defined database AdWorks  
RENAME DATABASE AdWorks to AdWorks2;  
  
```  
  
 При переименовании таблицы, все объекты и свойства, связанные с таблицей, обновляются для ссылки на новое имя таблицы. Например, в таблице определений, индексы, ограничения и разрешения обновляются. Представления не обновляются.  
  
### <a name="b-rename-a-table"></a>Б. Переименование таблицы  
 **ПРИМЕНЯЕТСЯ К:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 В этом примере таблицы Customer переименовывается в Customer1.  
  
```  
-- Rename the customer table  
RENAME OBJECT Customer TO Customer1;  
  
RENAME OBJECT mydb.dbo.Customer TO Customer1;  
```  
  
 При переименовании таблицы, все объекты и свойства, связанные с таблицей, обновляются для ссылки на новое имя таблицы. Например, в таблице определений, индексы, ограничения и разрешения обновляются. Представления не обновляются.  
   
  
### <a name="c-move-a-table-to-a-different-schema"></a>В. Перемещение таблицы в другую схему  
 **ПРИМЕНЯЕТСЯ К:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Если планируется переместить объект в другую схему, используйте [ALTER SCHEMA &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-schema-transact-sql.md). Например это перемещение элемента таблицы из схемы продуктов в схему dbo.  
  
```  
ALTER SCHEMA dbo TRANSFER OBJECT::product.item;  
```  
  
### <a name="d-terminate-sessions-before-renaming-a-table"></a>Г. Завершите сеансы, прежде чем переименовать таблицу  
 **ПРИМЕНЯЕТСЯ К:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Важно запомнить, не удается переименовать таблицу его во время использования. Переименование таблицы требуется монопольная блокировка таблицы. Если таблицы, может потребоваться прекратить сеанс, с помощью таблицы. Для завершения сеанса можно использовать команду KILL. Используйте инструкцию KILL осторожно, так как при завершении сеанса все незафиксированная работа будет выполнен откат. Сеансы в хранилище данных SQL добавляет префикс «SID». Необходимо включить это и номер сеанса при вызове команды KILL. Этот пример просматривает список активных или неактивных сеансов и затем завершает сеанс «SID1234».  
  
```  
-- View a list of the current sessions  
SELECT session_id, login_name, status   
FROM sys.dm_pdw_exec_sessions   
WHERE status='Active' OR status='Idle';  
  
-- Terminate a session using the session_id.  
KILL 'SID1234';  
```  
  
  

