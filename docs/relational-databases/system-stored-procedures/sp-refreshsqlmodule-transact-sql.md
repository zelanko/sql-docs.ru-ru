---
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: da2dacf6fcb34d5a5caba14ccb60cbb9eec43467
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529225"
---
# <a name="sprefreshsqlmodule-transact-sql"></a>sp_refreshsqlmodule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

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
`[ @name = ] 'module\_name'` — Имя хранимой процедуры, определяемой пользователем функции, представления, триггера DML, триггер DDL уровня базы данных или триггера DDL уровня сервера. *module_name* не может быть общеязыковая среда выполнения (CLR) хранимая процедура или функция среды CLR. *module_name* не может быть привязана к схеме. *module_name* — **nvarchar**, не имеет значения по умолчанию. *module_name* может быть составным идентификатором, но может ссылаться только на объекты в текущей базе данных.  
  
`[ , @namespace = ] ' \<class> '` — Класс указанного модуля. Когда *module_name* является триггером DDL, \<класс > является обязательным. *\<Класс >* — **nvarchar**(20). Допустимые входные значения:  
  
|||  
|-|-|  
|DATABASE_DDL_TRIGGER||  
|SERVER_DDL_TRIGGER|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_refreshsqlmodule** должен выполняться при изменении объектов модуля, которые влияют на его определение. В противном случае при обращении к модулю или при его вызове могут быть получены непредвиденные результаты. Для обновления представления можно использовать любой **sp_refreshsqlmodule** или **sp_refreshview** с теми же результатами.  
  
 **sp_refreshsqlmodule** не влияет на все разрешения, расширенные свойства или параметры SET, которые связаны с объектом.  
  
 Чтобы обновить триггер DDL уровня сервера, необходимо выполнить эту хранимую процедуру в контексте любой базы данных.  
  
> [!NOTE]  
>  Любые подписи, связанные с объектом, удаляются при выполнении **sp_refreshsqlmodule**.  
  
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
|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
```  
USE master;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddl_trig_database' , @namespace = 'SERVER_DDL_TRIGGER';  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [sp_refreshview (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
