---
title: "DENY, отказ в разрешениях на доступ к списку свойств поиска (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], permissions
- DENY statement, search property list permissions
- denying permissions [SQL Server], search property lists
- search property lists [SQL Server], permissions
ms.assetid: 96513cb4-a9c0-4834-97a4-ddc0777b8415
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c48a5b2b82fd052d6a854eb8b0496b0c730644a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="deny-search-property-list-permissions-transact-sql"></a>Разрешение на список свойств поиска DENY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Запрещает разрешения для списка свойств поиска.  
 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission [ ,...n ] ON  
        SEARCH PROPERTY LIST :: search_property_list_name  
    TO database_principal [ ,...n ] [ CASCADE ]  
    [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Имя разрешения. Допустимые сопоставления разрешений на защищаемые объекты описаны далее в подразделе «Примечания».  
  
ON SEARCH PROPERTY LIST **::***search_property_list_name*  
 Указывает список свойств поиска, для которого запрещается разрешение. Требуется квалификатор области (задается через знак ::).  
  
*database_principal*  
 Задает участника, для которого запрещается разрешение, — Участник может быть одним из следующих:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
*denying_principal*  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. Участник может быть одним из следующих:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="search-property-list-permissions"></a>Разрешения SEARCH PROPERTY LIST  
 Список свойств поиска — это защищаемый объект уровня базы данных, который находится в базе данных, которая является родительской в иерархии разрешений. В следующей таблице перечислены наиболее конкретные и ограниченные разрешения, которые можно запретить для списка свойств поиска, а также более общие разрешения, в которых неявно содержатся предыдущие разрешения.  
  
|Разрешение списка свойств поиска|Содержится в разрешении списка свойств поиска|Содержится в разрешении базы данных|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL на полнотекстовый каталог. При использовании параметра AS заданный участник должен владеть полнотекстовым каталогом.  
  
## <a name="see-also"></a>См. также:  
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.fn_my_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [GRANT, предоставление разрешений на список свойств поиска (Transact-SQL)](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [REVOKE, отмена разрешений на список свойств поиска (Transact-SQL)](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Поиск свойств документа с помощью списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
