---
title: DENY, запрет разрешений на полнотекстовые объекты (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], permissions
- denying permissions [SQL Server], fulll-text
- full-text catalogs [SQL Server], permissions
- full-text stoplist [SQL Server], permissions
- DENY statement, full-text permissions
ms.assetid: d86e9a1d-0938-4ec2-a169-2d0564f3642e
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d1418c1234e1723f0a4b662cadcf244a2aa86da3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33071911"
---
# <a name="deny-full-text-permissions-transact-sql"></a>DENY, запрет разрешений на полнотекстовые объекты (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения на полнотекстовый каталог и списки полнотекстовых стоп-слов.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission [ ,...n ] ON  
    FULLTEXT   
        {  
           CATALOG :: full-text_catalog_name  
           |  
           STOPLIST :: full-text_stoplist_name  
        }  
    TO database_principal [ ,...n ] [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Имя разрешения. Допустимые сопоставления разрешений на защищаемые объекты описаны далее в подразделе «Примечания».  
  
 ON FULLTEXT CATALOG **::***full-text_catalog_name*  
 Указывает полнотекстовый каталог, для которого запрещается разрешение. Квалификатор области **::** является обязательным.  
  
 ON FULLTEXT STOPLIST **::***full-text_stoplist_name*  
 Указывает список полнотекстовых стоп-слов, для которого запрещается разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, для которого запрещается разрешение. Это может быть:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
  
-   пользователь базы данных, не сопоставленный с участником на уровне сервера.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 *denying_principal*  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. Это может быть:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
  
-   пользователь базы данных, не сопоставленный с участником на уровне сервера.  
  
  
## <a name="fulltext-catalog-permissions"></a>Разрешения FULLTEXT CATALOG  
 Полнотекстовый каталог представляет собой защищаемый объект уровня базы данных, содержащийся в той базе данных, которая является его родителем в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запрещать для полнотекстового каталога, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение на полнотекстовый каталог|Содержится в разрешении полнотекстового каталога|Содержится в разрешении базы данных|  
|-----------------------------------|----------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="fulltext-stoplist-permissions"></a>Разрешения FULLTEXT STOPLIST  
 Список полнотекстовых стоп-слов является защищаемым объектом уровня базы данных, содержащимся в базе данных, являющейся его родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запрещать для списка полнотекстовых стоп-слов, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение на список полнотекстовых стоп-слов|Содержится в разрешении на список полнотекстовых стоп-слов|Содержится в разрешении базы данных|  
|------------------------------------|-----------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL на полнотекстовый каталог. При использовании параметра AS заданный участник должен владеть полнотекстовым каталогом.  
  
## <a name="see-also"></a>См. также:  
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.fn_my_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [GRANT, предоставление разрешений на полнотекстовые объекты (Transact-SQL)](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fulltext_catalogs (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sys.fulltext_stoplists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)  
  
  
