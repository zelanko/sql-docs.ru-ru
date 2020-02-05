---
title: HAS_PERMS_BY_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HAS_PERMS_BY_NAME
- HAS_PERMS_BY_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], verifying
- current permission status
- checking permission status
- verifying permission status
- testing permissions
- HAS_PERMS_BY_NAME function
ms.assetid: eaf8cc82-1047-4144-9e77-0e1095df6143
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1420c5f8a1a16dc7430af0b445a8464c16d1b763
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73982953"
---
# <a name="has_perms_by_name-transact-sql"></a>HAS_PERMS_BY_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Оценивает действующие разрешения текущего пользователя для защищаемого объекта. Связанная функция — [fn_my_permissions](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HAS_PERMS_BY_NAME ( securable , securable_class , permission    
    [ , sub-securable ] [ , sub-securable_class ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *securable*  
 Имя защищаемого объекта. Если защищаемым объектом является сам сервер или база данных, этому аргументу должно быть присвоено значение NULL. Аргумент *securable* является скалярным выражением типа **sysname**. Значение по умолчанию отсутствует.  
  
 *securable_class*  
 Имя класса защищаемого объекта, для которого проверяется разрешение. Аргумент *securable_class* является скалярным выражением типа **nvarchar(60)** .  
  
 В [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] аргумент securable_class должен быть установлен в одно из следующих значений: **DATABASE**, **OBJECT**, **ROLE**, **SCHEMA** или **USER**.  
  
 *permission*  
 Скалярное выражение типа **sysname**, отличное от NULL, представляющее проверяемое разрешение. Значение по умолчанию отсутствует. Имя разрешения ANY является шаблоном для подстановки.  
  
 *sub-securable*  
 Необязательное скалярное выражение типа **sysname**, представляющее имя защищаемой вложенной сущности, у которой проверяется разрешение. Значение по умолчанию — NULL.  
  
> [!NOTE]  
>  В версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выше во вложенных защищаемых объектах не могут использоваться скобки в форме **"[** _вложенное имя_ **]"** . Используйте вместо этого форму **'** _вложенное имя_ **'** .  
  
 *sub-securable_class*  
 Необязательное скалярное выражение типа **nvarchar(60)** , представляющее класс защищаемой вложенной сущности, для которой проверяется разрешение. Значение по умолчанию — NULL.  
  
 В [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] аргумент sub-securable_class является допустимым, только если аргумент securable_class имеет значение **OBJECT**. Если аргумент securable_class задан равным **OBJECT**, то аргумент sub-securable_class должен быть задан равным **COLUMN**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
 Возвращает значение NULL, если запрос завершается неудачей.  
  
## <a name="remarks"></a>Remarks  
 Эта встроенная функция проверяет, имеет ли текущий субъект определенное действующее разрешение для указанного защищаемого объекта. Функция HAS_PERMS_BY_NAME возвращает значение 1, если пользователь имеет действующее разрешение на защищаемый объект, значение 0, если пользователь не имеет действующего разрешения на защищаемый объект, либо значение NULL, если класс защищаемого объекта или разрешение недопустимы. Допустимыми являются следующие действующие разрешения.  
  
-   Действующее разрешение, предоставленное непосредственно участнику.  
  
-   Действующее разрешение, следующее из разрешений более высокого уровня, которыми обладает участник.  
  
-   Действующее разрешение, предоставленное роли или группе, членом которой является участник.  
  
-   Действующее разрешение, принадлежащее роли или группе, членом которой является участник.  
  
 Оценка разрешений всегда выполняется в контексте безопасности участника. Чтобы определить наличие действующего разрешения у какого-либо другого пользователя, вызывающая сторона должна обладать разрешением IMPERSONATE для данного пользователя.  
  
 Для объектов на уровне схем допустимы одно-, двух- и трехкомпонентные непустые имена. Для объектов на уровне базы данных допустимы одночастные имена, причем значение NULL означает текущую базу данных. Для самого сервера значение NULL является обязательным и означает текущий сервер. Данная функция не может проверить разрешения связанного сервера или пользователя Windows, для которого не создан участник уровня сервера.  
  
 Приведенный ниже запрос возвращает список встроенных классов защищаемых объектов:  
  
```  
SELECT class_desc FROM sys.fn_builtin_permissions(default);  
```  
  
 Используются следующие параметры сортировки.  
  
-   Параметры сортировки текущей базы данных: защищаемые объекты на уровне базы данных, куда относятся защищаемые объекты, не входящие в схему; одно- или двухкомпонентные защищаемые объекты схемы; целевая база данных (если используется трехкомпонентное имя).  
  
-   Параметры сортировки базы данных master: защищаемые объекты на уровне сервера.  
  
-   ANY не поддерживается в проверке уровня столбца. Необходимо указать соответствующие разрешения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-do-i-have-the-server-level-view-server-state-permission"></a>A. Наличие разрешения VIEW SERVER STATE на уровне сервера  
  
**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий
  
```  
SELECT HAS_PERMS_BY_NAME(null, null, 'VIEW SERVER STATE');  
```  
  
### <a name="b-am-i-able-to-impersonate-server-principal-ps"></a>Б. Наличие разрешения IMPERSONATE для олицетворения участника на уровне сервера Ps  
  
**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий
  
```  
SELECT HAS_PERMS_BY_NAME('Ps', 'LOGIN', 'IMPERSONATE');  
```  
  
### <a name="c-do-i-have-any-permissions-in-the-current-database"></a>В. Наличие любых разрешений в текущей базе данных  
  
```  
SELECT HAS_PERMS_BY_NAME(db_name(), 'DATABASE', 'ANY');  
```  
  
### <a name="d-does-database-principal-pd-have-any-permission-in-the-current-database"></a>Г. Наличие у участника базы данных Pd любых разрешений в текущей базе данных  
 Предположим, что участник обладает разрешением IMPERSONATE для участника `Pd`.  
  
```  
EXECUTE AS user = 'Pd'  
GO  
SELECT HAS_PERMS_BY_NAME(db_name(), 'DATABASE', 'ANY');  
GO  
REVERT;  
GO  
```  
  
### <a name="e-can-i-create-procedures-and-tables-in-schema-s"></a>Д. Возможность создавать процедуры и таблицы в схеме S  
 Для выполнения следующего примера необходимо наличие разрешения `ALTER` в схеме `S` и разрешения `CREATE PROCEDURE` в базе данных, а также в таблицах.  
  
```  
SELECT HAS_PERMS_BY_NAME(db_name(), 'DATABASE', 'CREATE PROCEDURE')  
    & HAS_PERMS_BY_NAME('S', 'SCHEMA', 'ALTER') AS _can_create_procs,  
    HAS_PERMS_BY_NAME(db_name(), 'DATABASE', 'CREATE TABLE') &  
    HAS_PERMS_BY_NAME('S', 'SCHEMA', 'ALTER') AS _can_create_tables;  
```  
  
### <a name="f-which-tables-do-i-have-select-permission-on"></a>Е. Таблицы, для которых пользователь имеет разрешение SELECT  
  
```  
SELECT HAS_PERMS_BY_NAME  
(QUOTENAME(SCHEMA_NAME(schema_id)) + '.' + QUOTENAME(name),   
    'OBJECT', 'SELECT') AS have_select, * FROM sys.tables  
```  
  
### <a name="g-do-i-have-insert-permission-on-the-salesperson-table-in-adventureworks2012"></a>Ж. Наличие разрешения INSERT для таблицы SalesPerson в базе данных AdventureWorks2012  
 В следующем примере предполагается, что текущим контекстом базы данных является `AdventureWorks2012`, а также используется двухкомпонентное имя.  
  
```  
SELECT HAS_PERMS_BY_NAME('Sales.SalesPerson', 'OBJECT', 'INSERT');  
```  
  
 В следующем примере используется трехкомпонентное имя; какие-либо предположения о контексте текущей базы данных отсутствуют.  
  
```  
SELECT HAS_PERMS_BY_NAME('AdventureWorks2012.Sales.SalesPerson',   
    'OBJECT', 'INSERT');  
```  
  
### <a name="h-which-columns-of-table-t-do-i-have-select-permission-on"></a>З. Столбцы таблицы T, для которых пользователь имеет разрешение SELECT  
  
```  
SELECT name AS column_name,   
    HAS_PERMS_BY_NAME('T', 'OBJECT', 'SELECT', name, 'COLUMN')   
    AS can_select   
    FROM sys.columns AS c   
    WHERE c.object_id=object_id('T');  
```  
  
## <a name="see-also"></a>См. также:  
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Иерархия разрешений (ядро СУБД)](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
  
  
