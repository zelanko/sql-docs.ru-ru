---
title: DENY, запрет разрешений на схему (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], schemas
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
- DENY statement, schemas
ms.assetid: 300a67c4-d226-4653-9e9f-7ae4d53fcf33
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 37b88f07571029e39080f38c1406ab89ec73b0a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62910166"
---
# <a name="deny-schema-permissions-transact-sql"></a>DENY, запрет разрешений на схему (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Запрещает разрешения на схему.  
  

![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DENY permission  [ ,...n ] } ON SCHEMA :: schema_name  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
*permission*  
Указывает разрешение, которое может быть запрещено на схему. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
ON SCHEMA **::** schema *_name*  
Указывает схему, на которую запрещается разрешение. Квалификатор области **::** является обязательным.  
  
*database_principal*  
Указывает участника, для которого запрещается разрешение. *database_principal* может быть одним из следующих:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
-   пользователь базы данных, не сопоставленный с сервером-участником.  
  
CASCADE  
Запрещает разрешение для любых других участников, которым *database_principal* явно предоставил разрешение.
  
*denying_principal*  
Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. *denying_principal* может быть одним из следующих:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
-   пользователь базы данных, не сопоставленный с сервером-участником.  
  
## <a name="remarks"></a>Remarks  
Схема — это защищаемый объект уровня базы данных. Она находится в базе данных, которая является родительской в иерархии разрешений. Наиболее часто указываемые и ограниченные разрешения, которые могут быть запрещены в схеме, перечислены в следующей таблице. В таблице показаны наиболее общие разрешения, неявно их содержащие.  
  
|Разрешение схемы|Содержится в разрешении схемы|Содержится в разрешении базы данных|  
|-----------------------|----------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SCHEMA|  
|CONTROL|CONTROL|CONTROL|  
|CREATE SEQUENCE|ALTER|ALTER ANY SCHEMA|  
|DELETE|CONTROL|DELETE|  
|EXECUTE|CONTROL|EXECUTE|  
|INSERT|CONTROL|INSERT|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|CONTROL|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
Требуется разрешение CONTROL для схемы. Если указан параметр AS, указанный участник должен быть владельцем схемы.  
  
## <a name="see-also"></a>См. также:  
[CREATE SCHEMA (Transact-SQL)](../../t-sql/statements/create-schema-transact-sql.md)   
[DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
[Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
[Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
[sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
[sys.fn_my_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
[HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
