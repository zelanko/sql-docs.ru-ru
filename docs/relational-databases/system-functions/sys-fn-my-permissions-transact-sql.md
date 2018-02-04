---
title: "sys.fn_my_permissions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fn_my_permissions_TSQL
- fn_my_permissions_TSQL
- sys.fn_my_permissions
- fn_my_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- fn_my_permissions function
- sys.fn_my_permissions function
ms.assetid: 30f97f00-03d8-443a-9de9-9ec420b7699b
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9eb23a2de7fda489b205f1eaf89c124068be63b3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysfnmypermissions-transact-sql"></a>sys.fn_my_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список разрешений на защищаемый объект, фактически предоставленных участнику. Связанная функция — [HAS_PERMS_BY_NAME](../../t-sql/functions/has-perms-by-name-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_my_permissions ( securable , 'securable_class' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *защищаемый объект*  
 Имя защищаемого объекта. Если защищаемым объектом является сам сервер или база данных, то этому аргументу должно быть присвоено значение NULL. *защищаемый объект* является скалярным выражением типа **sysname**. *защищаемый объект* может быть составным именем.  
  
 "*securable_class*"  
 Имя класса защищаемых объектов, для которого перечислены разрешения. *securable_class* — **sysname**. *securable_class* должен быть одним из следующих: РОЛИ приложения, сборки, АСИММЕТРИЧНЫЙ ключ, СЕРТИФИКАТ, КОНТРАКТА, базы данных, конечной ТОЧКИ, FULLTEXT CATALOG, имени входа, ТИПАМ сообщений, ОБЪЕКТА, REMOTE SERVICE BINDING, РОЛИ, МАРШРУТА, СХЕМЫ, сервера и службы , СИММЕТРИЧНЫЙ КЛЮЧ, ТИП, ПОЛЬЗОВАТЕЛЬ, КОЛЛЕКЦИИ СХЕМ XML.  
  
## <a name="columns-returned"></a>Возвращаемые столбцы  
 В следующей таблице перечислены столбцы, **fn_my_permissions** возвращает. Каждая возвращаемая строка описывает разрешение относительно защищаемого объекта в текущем контексте безопасности. Возвращает NULL в случае неудачного завершения запроса.  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|entity_name|**sysname**|Имя защищаемого объекта, на который предоставлены перечисленные разрешения.|  
|subentity_name|**sysname**|Имя столбца, если у защищаемого объекта есть столбцы, в противном случае — NULL.|  
|permission_name|**nvarchar**|Имя разрешения.|  
  
## <a name="remarks"></a>Remarks  
 Эта функция возвращает список действующих разрешений вызывающего участника в отношении указанного защищаемого объекта. Действующим разрешением будет одно из следующих:  
  
-   Действующее разрешение, предоставленное непосредственно участнику.  
  
-   Действующее разрешение, следующее из разрешений более высокого уровня, которыми обладает участник.  
  
-   Действующее разрешение, предоставленное роли или группе, членом которой является участник.  
  
-   Действующее разрешение, принадлежащее роли или группе, членом которой является участник.  
  
 Оценка разрешений всегда выполняется в контексте безопасности участника. Для определения того, имеют ли какие-либо другие участники действующее разрешение, вызывающая сторона должна иметь разрешение IMPERSONATE в отношении такого участника.  
  
 Для объектов на уровне схем допустимы одно-, двух- и трехкомпонентные непустые имена. Для сущностей уровня базы данных допустимо имя одной части, с значение null означает «*текущей базы данных*». Для самого сервера значение NULL является обязательным и означает текущий сервер. **fn_my_permissions** не может проверить разрешения на связанном сервере.  
  
 Приведенный ниже запрос возвращает список встроенных классов защищаемых объектов:  
  
```  
SELECT DISTINCT class_desc FROM fn_builtin_permissions(default)  
    ORDER BY class_desc;  
GO  
```  
  
 Если указано в качестве значения по умолчанию *защищаемый объект* или *securable_class*, значение будет интерпретироваться как значение NULL.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-effective-permissions-on-the-server"></a>A. Перечисление действующих разрешений на сервере  
 Следующий пример возвращает список действующих разрешений вызывающей стороны на сервере.  
  
```  
SELECT * FROM fn_my_permissions(NULL, 'SERVER');  
GO  
```  
  
### <a name="b-listing-effective-permissions-on-the-database"></a>Б. Перечисление действующих разрешений в базе данных  
 Следующий пример возвращает список действующих разрешений для вызывающей стороны в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions (NULL, 'DATABASE');  
GO  
```  
  
### <a name="c-listing-effective-permissions-on-a-view"></a>В. Перечисление действующих разрешений в представлении  
 Следующий пример возвращает список действующих разрешений вызывающей стороны в представлении `vIndividualCustomer` в схеме `Sales` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('Sales.vIndividualCustomer', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;   
GO   
```  
  
### <a name="d-listing-effective-permissions-of-another-user"></a>Г. Перечисление действующих разрешений другого пользователя  
 Следующий пример возвращает список действующих разрешений пользователя базы данных `Wanida` для таблицы `Employee` в схеме `HumanResources` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Для вызывающей стороны требуется разрешение IMPERSONATE для пользователя `Wanida`.  
  
```  
EXECUTE AS USER = 'Wanida';  
SELECT * FROM fn_my_permissions('HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
### <a name="e-listing-effective-permissions-on-a-certificate"></a>Д. Перечисление действующих разрешений для сертификата  
 Следующий пример возвращает список действующих разрешений вызывающей стороны для сертификата с именем `Shipping47` в текущей базе данных.  
  
```  
SELECT * FROM fn_my_permissions('Shipping47', 'CERTIFICATE');  
GO  
```  
  
### <a name="f-listing-effective-permissions-on-an-xml-schema-collection"></a>Е. Перечисляет действующие разрешения для коллекции XML-схем  
 Следующий пример возвращает список действующих разрешений вызывающей стороны на коллекцию схем XML с именем `ProductDescriptionSchemaCollection` в [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных.  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('ProductDescriptionSchemaCollection',  
    'XML SCHEMA COLLECTION');  
GO  
```  
  
### <a name="g-listing-effective-permissions-on-a-database-user"></a>Ж. Перечисление действующих разрешений для пользователя базы данных  
 Следующий пример возвращает список действующих разрешений вызывающей стороны для пользователя по имени `MalikAr` в текущей базе данных.  
  
```  
SELECT * FROM fn_my_permissions('MalikAr', 'USER');  
GO  
```  
  
### <a name="h-listing-effective-permissions-of-another-login"></a>З. Перечисление действующих разрешений другого имени входа  
 Следующий пример возвращает список действующих разрешений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа `WanidaBenshoof` для таблицы `Employee` в схеме `HumanResources` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Для вызывающей стороны требуется разрешение IMPERSONATE для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `WanidaBenshoof`.  
  
```  
EXECUTE AS LOGIN = 'WanidaBenshoof';  
SELECT * FROM fn_my_permissions('AdventureWorks2012.HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Иерархия разрешений (ядро СУБД)](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [ВЫПОЛНЕНИЕ AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
