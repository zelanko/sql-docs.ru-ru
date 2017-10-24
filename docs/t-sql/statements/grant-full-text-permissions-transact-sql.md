---
title: "Разрешения GRANT Full-Text (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], full-text
- full-text search [SQL Server], permissions
- full-text catalogs [SQL Server], permissions
- full-text stoplist [SQL Server], permissions
- GRANT statement, full-text permissions
ms.assetid: fdb64e09-222a-47fe-b08b-999264ca261d
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 624b779b088008076360e12ed96c450fc3e91b50
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grant-full-text-permissions-transact-sql"></a>GRANT, предоставление разрешений на полнотекстовые объекты (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Предоставляет разрешения на полнотекстовый каталог или список полнотекстовых стоп-слов.  
  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
GRANT permission [ ,...n ] ON  
    FULLTEXT   
        {  
           CATALOG :: full-text_catalog_name  
           |  
           STOPLIST :: full-text_stoplist_name  
        }  
    TO database_principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Имя разрешения. Допустимые сопоставления разрешений на защищаемые объекты описаны далее в подразделе «Примечания».  
  
 НА ПОЛНОТЕКСТОВЫЙ КАТАЛОГ **::***full text_catalog_name*  
 Указывает полнотекстовый каталог, на который предоставляется разрешение. Квалификатор области **::** является обязательным.  
  
 НА ПОЛНОТЕКСТОВЫЙ список стоп-СЛОВ **::***full text_stoplist_name*  
 Указывает список полнотекстовых стоп-слов, на который предоставляется разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Участник, которому предоставляется разрешение. Это может быть:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
AS *granting_principal*  
 Указывает участника, от которого участник, выполняющий данный запрос, наследует право на предоставление разрешения. Это может быть:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный асимметричному ключу;  
-   пользователь базы данных, не сопоставленный участнику [системы безопасности] на уровне сервера.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="fulltext-catalog-permissions"></a>Разрешения FULLTEXT CATALOG  
 Полнотекстовый каталог представляет собой защищаемый объект уровня базы данных, содержащийся в той базе данных, которая является его родителем в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно предоставлять на полнотекстовый каталог, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение на полнотекстовый каталог|Содержится в разрешении полнотекстового каталога|Содержится в разрешении базы данных|  
|-----------------------------------|----------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="fulltext-stoplist-permissions"></a>Разрешения FULLTEXT STOPLIST  
 Список полнотекстовых стоп-слов является защищаемым объектом уровня базы данных, содержащимся в базе данных, являющейся его родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно предоставлять на список полнотекстовых стоп-слов, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение на список полнотекстовых стоп-слов|Содержится в разрешении на список полнотекстовых стоп-слов|Содержится в разрешении базы данных|  
|------------------------------------|-----------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое.  
  
 Если используется параметр AS, налагаются следующие дополнительные требования.  
  
|AS *granting_principal*|Необходимо дополнительное разрешение|  
|------------------------------|------------------------------------|  
|Пользователь базы данных|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный имени входа Windows|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный группе Windows|Членство в группе Windows, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный сертификату|Членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный асимметричному ключу|Членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, не сопоставленный ни с одним участником на уровне сервера|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Роль базы данных|Разрешение ALTER на роль, членство в предопределенной роли базы данных db_securityadmin, предопределенной роли базы данных db_owner или предопределенной роли сервера sysadmin.|  
|Роль приложения|Разрешение ALTER на роль, членство в предопределенной роли базы данных db_securityadmin, предопределенной роли базы данных db_owner или предопределенной роли сервера sysadmin.|  
  
 Владельцы объектов могут предоставлять разрешения на объекты, которыми они владеют. Участники, имеющие разрешение CONTROL на защищаемый объект, могут предоставлять разрешение на этот защищаемый объект.  
  
 Участники, которым предоставлено разрешение CONTROL SERVER, такие как члены предопределенной роли сервера &lt;legacyBold&gt;sysadmin&lt;/legacyBold&gt;, могут предоставлять любое разрешение на любой защищаемый объект сервера. Участники, получившие разрешение CONTROL на базу данных, такие как члены предопределенной роли базы данных db_owner, могут предоставлять любое разрешение на любой защищаемый объект в базе данных. Владельцы разрешения CONTROL, связанного со схемой, могут предоставлять любые разрешения на работу с любыми объектами, содержащимися в данной схеме.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-permissions-to-a-full-text-catalog"></a>A. Предоставление разрешений на полнотекстовый каталог  
 В следующем примере пользователю `Ted` предоставляется разрешение `CONTROL` на полнотекстовый каталог `ProductCatalog`.  
  
```  
GRANT CONTROL  
    ON FULLTEXT CATALOG :: ProductCatalog  
    TO Ted ;  
```  
  
### <a name="b-granting-permissions-to-a-stoplist"></a>Б. Предоставление разрешений на список стоп-слов  
 В следующем примере пользователю `Mary` предоставляется разрешение `VIEW DEFINITION` на список полнотекстовых стоп-слов `ProductStoplist`.  
  
```  
GRANT VIEW DEFINITION  
    ON FULLTEXT STOPLIST :: ProductStoplist  
    TO Mary ;  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ РОЛЬ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE FULLTEXT CATALOG #40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [СОЗДАТЬ ПОЛНОТЕКСТОВЫЙ список стоп-СЛОВ &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sys.fulltext_stoplists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)  
  
  

