---
title: RENAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/21/2019
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 0907cfd9-33a6-4fa6-91da-7d6679fee878
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 624131beece632cffd13bde3d6ad378f67b3a340
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68141273"
---
# <a name="rename-transact-sql"></a>RENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Переименовывает созданную пользователем таблицу в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Переименовывает созданную пользователем таблицу или базу данных в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].

> [!NOTE]
> Чтобы переименовать базу данных в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], используйте инструкцию [ALTER DATABASE (хранилище данных SQL Azure)](alter-database-transact-sql.md?view=aps-pdw-2016-au7). Чтобы переименовать базу данных в службе базы данных SQL Azure, используйте инструкцию [ALTER DATABASE (база данных SQL Azure)](alter-database-transact-sql.md?view=azuresqldb-mi-current). Чтобы переименовать базу данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте хранимую процедуру [sp_renamedb](../../relational-databases/system-stored-procedures/sp-renamedb-transact-sql.md).

## <a name="syntax"></a>Синтаксис

```
-- Syntax for Azure SQL Data Warehouse

-- Rename a table.
RENAME OBJECT [::] [ [ database_name . [schema_name ] ] . ] | [schema_name . ] ] table_name TO new_table_name
[;]

```

```
-- Syntax for Analytics Platform System

-- Rename a table
RENAME OBJECT [::] [ [ database_name . [ schema_name ] . ] | [ schema_name . ] ] table_name TO new_table_name
[;]

-- Rename a database
RENAME DATABASE [::] database_name TO new_database_name
[;]
```

## <a name="arguments"></a>Аргументы

RENAME OBJECT [::] [ [*database_name* . [ *schema_name* ] . ] | [ *schema_name* . ] ]*table_name* TO *new_table_name* — 
**применимо к**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Изменение имени определяемой пользователем таблицы. Указание таблицы для переименования с именем, состоящим из одной, двух или трех частей. Указание *имени_новой_таблицы*, состоящего из одной части.

RENAME DATABASE [::] [ *имя_базы_данных* TO *новое_имя_базы_данных* — 
**применимо к** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Изменение имени пользовательской базы данных с *имени_базы_данных* на *новое_имя_базы_данных*. Следующие имена баз данных являются [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]зарезервированными и не могут использоваться в качестве нового имени базы данных:

- master
- model
- msdb
- tempdb
- pdwtempdb1
- pdwtempdb2
- DWConfiguration
- DWDiagnostics
- DWQueue

## <a name="permissions"></a>Разрешения

Для выполнения этой команды требуется следующее разрешение:

- Разрешение **ALTER** на таблицу

## <a name="limitations-and-restrictions"></a>Ограничения

### <a name="cannot-rename-an-external-table-indexes-or-views"></a>Невозможно переименовать внешние таблицы, индексы и представления

Вы не можете переименовать внешние таблицы, индексы и представления. Вместо переименования можно удалить внешнюю таблицу, индекс или представление и затем создать этот объект повторно с новым именем.

### <a name="cannot-rename-a-table-in-use"></a>Невозможно переименовать используемую таблицу

Вы не можете переименовать таблицу или базу данных во время использования. Для переименования таблицы требуется монопольная блокировка таблицы. Если таблица используется, может потребоваться завершить сеансы, которые используют таблицу. Для завершения сеанса можно использовать команду KILL. Используйте инструкцию KILL осторожно, так как при завершении сеанса для всей незафиксированной работы будет выполнен откат. К сеансам в хранилище данных SQL добавляется префикс "SID". Префикс "SID" и номер сеанса необходимо указать при вызове команды KILL. В этом примере мы получаем список активных или неактивных сеансов и затем завершаем сеанс "SID1234".

### <a name="views-are-not-updated"></a>Представления не обновляются

При переименовании базы данных все представления, в которых используется предыдущее имя базы данных, станут недействительными. Это поведение относится к представлениям как внутри, так и вне базы данных. Например, при переименовании базы данных Sales представления, содержащие `SELECT * FROM Sales.dbo.table1`, станут недействительными. Чтобы устранить эту проблему, старайтесь не использовать имена из трех частей в представлениях или обновите представления так, чтобы в них использовалось новое имя базы данных.

При переименовании таблицы обновления имени таблицы в представлениях не происходит. Все представления внутри или вне базы данных, которые ссылаются на предыдущее имя таблицы, станут недействительными. Чтобы устранить эту проблему, обновите представления так, чтобы в них использовалось новое имя базы данных.

## <a name="locking"></a>Блокировка

Для переименования таблицы необходима совмещаемая блокировка для объекта базы данных, совмещаемая блокировка для объекта СХЕМЫ и монопольная блокировка таблицы.

## <a name="examples"></a>Примеры

### <a name="a-rename-a-database"></a>A. Переименование базы данных

**Применимо к** только [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

В этом примере мы переименовываем пользовательскую базу данных AdWorks в AdWorks2.

```sql
-- Rename the user defined database AdWorks
RENAME DATABASE AdWorks to AdWorks2;

```

 При переименовании таблицы все объекты и свойства, связанные с этой таблицей, обновляются, так чтобы в них использовалось новое имя таблицы. Например, обновляются определения таблиц, индексы, ограничения и разрешения. Представления не обновляются.

### <a name="b-rename-a-table"></a>Б. Переименование таблицы

**Применимо к**: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

В этом примере мы переименовываем таблицу Customer в Customer1.

```sql
-- Rename the customer table
RENAME OBJECT Customer TO Customer1;

RENAME OBJECT mydb.dbo.Customer TO Customer1;
```

При переименовании таблицы все объекты и свойства, связанные с этой таблицей, обновляются, так чтобы в них использовалось новое имя таблицы. Например, обновляются определения таблиц, индексы, ограничения и разрешения. Представления не обновляются.

### <a name="c-move-a-table-to-a-different-schema"></a>В. Перемещение таблицы в другую схему

**Применимо к**: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Если вы хотите переместить объект в другую схему, используйте инструкцию [ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md). Например, следующая инструкция перемещает элемент таблицы из схемы product в схему dbo.

```sql
ALTER SCHEMA dbo TRANSFER OBJECT::product.item;
```

### <a name="d-terminate-sessions-before-renaming-a-table"></a>Г. Завершение сеансов перед переименованием таблицы

**Применимо к**: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Важно помнить, что вы не можете переименовать таблицу, которая используется. Для переименования таблицы требуется монопольная блокировка таблицы. Если таблица используется, может потребоваться завершить сеансы, которые используют таблицу. Для завершения сеанса можно использовать команду KILL. Используйте инструкцию KILL осторожно, так как при завершении сеанса для всей незафиксированной работы будет выполнен откат. К сеансам в хранилище данных SQL добавляется префикс "SID". Префикс "SID" и номер сеанса потребуется указать при вызове команды KILL. В этом примере мы получаем список активных или неактивных сеансов и затем завершаем сеанс "SID1234".

```sql
-- View a list of the current sessions
SELECT session_id, login_name, status
FROM sys.dm_pdw_exec_sessions
WHERE status='Active' OR status='Idle';

-- Terminate a session using the session_id.
KILL 'SID1234';
```