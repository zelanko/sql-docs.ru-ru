---
description: sp_refreshsqlmodule (Transact-SQL)
title: sp_refreshsqlmodule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refreshsqlmodule_TSQL
- sp_refreshsqlmodule
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- metadata [SQL Server], triggers
- metadata [SQL Server], views
- triggers [SQL Server], refreshing metadata
- views [SQL Server], refreshing metadata
- sp_refreshsqlmodule
- metadata [SQL Server], functions
- stored procedures [SQL Server], refreshing metadata
- user-defined functions [SQL Server], refreshing metadata
ms.assetid: f0022a05-50dd-4620-961d-361b1681d375
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c2621ffb96ad93d75e5b59e11963f93bf0f32eb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485900"
---
# <a name="sp_refreshsqlmodule-transact-sql"></a>sp_refreshsqlmodule (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Обновляет метаданные для указанной не привязанной к схеме хранимой процедуры, определяемой пользователем функции, представления, триггера DML, а также триггера DDL уровня базы данных или сервера в текущей базе данных. Непрерывные метаданные для этих объектов, такие как типы данных параметров, могут устаревать по причине изменений их базовых объектов.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_refreshsqlmodule [ @name = ] 'module_name'   
    [ , [ @namespace = ] ' <class> ' ]  
  
<class> ::=  
{  
  | DATABASE_DDL_TRIGGER  
  | SERVER_DDL_TRIGGER  
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'module\_name'` Имя хранимой процедуры, определяемой пользователем функции, представления, триггера DML, триггера DDL уровня базы данных или триггера DDL уровня сервера. *module_name* не может быть хранимой процедурой среды CLR или функцией CLR. *module_name* не могут быть привязаны к схеме. *module_name* имеет тип **nvarchar**и не имеет значения по умолчанию. *module_name* может быть составным идентификатором, но может ссылаться только на объекты в текущей базе данных.  
  
`[ , @namespace = ] ' \<class> '` Класс указанного модуля. Если *module_name* является триггером DDL, \<class> требуется. *\<class>* имеет тип **nvarchar**(20). Допустимые входные значения:  

* DATABASE_DDL_TRIGGER

* SERVER_DDL_TRIGGER — **применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздним версиям.

## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 **sp_refreshsqlmodule** должны выполняться при внесении изменений в объекты, лежащие в основе модуля, который влияет на его определение. В противном случае при обращении к модулю или при его вызове могут быть получены непредвиденные результаты. Чтобы обновить представление, можно использовать либо **sp_refreshsqlmodule** , либо **sp_refreshview** с теми же результатами.  
  
 **sp_refreshsqlmodule** не влияет на разрешения, расширенные свойства или параметры SET, связанные с объектом.  
  
 Чтобы обновить триггер DDL уровня сервера, необходимо выполнить эту хранимую процедуру в контексте любой базы данных.  
  
> [!NOTE]  
>  Все подписи, связанные с объектом, удаляются при запуске **sp_refreshsqlmodule**.  
  
## <a name="permissions"></a>Разрешения  
 При ссылке объекта на модуль необходимо разрешение ALTER, а при использовании модулем определяемых пользователем типов данных CLR и коллекций схем XML на них требуется разрешение REFERENCES. Если указанный модуль является триггером DDL уровня базы данных, то для текущей базы данных требуется разрешение ALTER ANY DATABASE DDL TRIGGER. Если указанный модуль является триггером DDL уровня сервера, необходимо разрешение CONTROL SERVER.  
  
 Кроме того, для модулей, определенных при помощи предложения EXECUTE AS, на указанном участнике необходимо разрешение IMPERSONATE. Обычно обновление объекта не изменяет его участника EXECUTE AS, если модуль не был определен при помощи предложения EXECUTE AS USER, и имя пользователя участника не является результатом пользователя, отличного от пользователя в момент создания модуля.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-refreshing-a-user-defined-function"></a>A. Обновление определяемой пользователем функции  
 В следующем примере показано обновление определяемой пользователем функции. В примере создается псевдоним типа данных `mytype` и определяемая пользователем функция `to_upper`, использующая `mytype`. Затем тип данных `mytype` переименовывается в `myoldtype`, и создается новый тип данных `mytype` с другим определением. Функция `dbo.to_upper` обновляется таким образом, что она будет ссылаться на новую реализацию `mytype` вместо прежней.  
  
```  
-- Create an alias type.  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT 'mytype' FROM sys.types WHERE name = 'mytype')  
DROP TYPE mytype;  
GO  
  
CREATE TYPE mytype FROM nvarchar(5);  
GO  
  
IF OBJECT_ID ('dbo.to_upper', 'FN') IS NOT NULL  
DROP FUNCTION dbo.to_upper;  
GO  
  
CREATE FUNCTION dbo.to_upper (@a mytype)  
RETURNS mytype  
WITH ENCRYPTION  
AS  
BEGIN  
RETURN upper(@a)  
END;  
GO  
  
SELECT dbo.to_upper('abcde');  
GO  
  
-- Increase the length of the alias type.  
sp_rename 'mytype', 'myoldtype', 'userdatatype';  
GO  
  
CREATE TYPE mytype FROM nvarchar(10);  
GO  
  
-- The function parameter still uses the old type.  
SELECT name, type_name(user_type_id)   
FROM sys.parameters   
WHERE object_id = OBJECT_ID('dbo.to_upper');  
GO  
  
SELECT dbo.to_upper('abcdefgh'); -- Fails because of truncation  
GO  
  
-- Refresh the function to bind to the renamed type.  
EXEC sys.sp_refreshsqlmodule 'dbo.to_upper';  
  
-- The function parameters are now bound to the correct type and the statement works correctly.  
SELECT name, type_name(user_type_id) FROM sys.parameters  
WHERE object_id = OBJECT_ID('dbo.to_upper');  
GO  
  
SELECT dbo.to_upper('abcdefgh');  
GO  
```  
  
### <a name="b-refreshing-a-database-level-ddl-trigger"></a>Б. Обновление триггера DDL уровня базы данных  
 В представленном ниже примере обновляется триггер DDL уровня базы данных.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddlDatabaseTriggerLog' , @namespace = 'DATABASE_DDL_TRIGGER';  
GO  
```  
  
### <a name="c-refreshing-a-server-level-ddl-trigger"></a>В. Обновление триггера DDL уровня сервера  
 В представленном ниже примере обновляется триггер DDL уровня сервера.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий.|  
  
```  
USE master;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddl_trig_database' , @namespace = 'SERVER_DDL_TRIGGER';  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_refreshview (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
