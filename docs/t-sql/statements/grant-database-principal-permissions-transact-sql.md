---
title: "Предоставление разрешений участникам базы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/12/2017
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
- database roles [SQL Server], permissions
- permissions [SQL Server], database roles
- granting permissions [SQL Server], database users
- granting permissions [SQL Server], application roles
- granting permissions [SQL Server], database roles
- database user permissions [SQL Server]
- permissions [SQL Server], application roles
- permissions [SQL Server], database users
- GRANT statement, users
- GRANT statement, roles
- application roles [SQL Server], permissions
ms.assetid: 012588a2-cbe1-48f0-a731-b4a2b83203d5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a2d78167459a509d788e65ad31d4660298107558
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grant-database-principal-permissions-transact-sql"></a>GRANT, предоставление разрешений на участника базы данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Предоставление разрешений пользователям базы данных, ролям базы данных или ролям приложения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
GRANT permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
     | [ ROLE :: database_role ]  
     | [ APPLICATION ROLE :: application_role ]  
    }  
    TO <database_principal> [ ,...n ]  
       [ WITH GRANT OPTION ]  
       [ AS <database_principal> ]  
  
<database_principal> ::=  
    Database_user   
  | Database_role   
  | Application_role   
  | Database_user_mapped_to_Windows_User   
  | Database_user_mapped_to_Windows_Group   
  | Database_user_mapped_to_certificate   
  | Database_user_mapped_to_asymmetric_key   
  | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение, которое может быть предоставлено участнику базы данных. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 ПОЛЬЗОВАТЕЛЬ::*пользователь_базы_данных*  
 Указывает класс и имя пользователя, которому предоставляется разрешение. Требуется квалификатор области (::).  
  
 РОЛЬ::*database_role*  
 Указывает класс и имя роли, которой предоставляется разрешение. Требуется квалификатор области (::).  
  
 РОЛЬ приложения::*application_role*  
   
 Указывает класс и имя роли приложения, которой предоставляется разрешение. Требуется квалификатор области (::).  
  
 WITH GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
 AS \<database_principal >  
 Указывает участника, от которого участник, выполняющий данный запрос, наследует право на предоставление разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
 Задает имя базы данных пользователя, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Сведения об участниках базы данных можно увидеть в [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) представления каталога. Сведения о разрешениях уровня базы данных можно увидеть в [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) представления каталога.  
  
## <a name="database-user-permissions"></a>Разрешения пользователя базы данных  
 Пользователь базы данных — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно предоставлять пользователю базы данных, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение пользователя базы данных|Содержится в разрешении пользователя базы данных|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>Разрешения роли базы данных  
 Роль базы данных — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно предоставлять роли базы данных, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение роли базы данных|Содержится в разрешении роли базы данных|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>Разрешения роли приложения  
 Роль приложения — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно предоставлять роли приложения, перечислены далее вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение роли приложения|Содержится в разрешении роли приложения|Содержится в разрешении базы данных|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое.  
  
 При использовании параметра AS налагаются следующие дополнительные требования.  
  
|AS *granting_principal*|Необходимо дополнительное разрешение|  
|------------------------------|------------------------------------|  
|Пользователь базы данных|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных сопоставлен с пользователем Windows|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный группе Windows|Членство в группе Windows, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный сертификату|Членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный асимметричному ключу|Членство в роли базы данных db_securityadminfixed db_owner членом фиксированной роли базы данных или членство в фиксированной серверной роли sysadmin.|  
|Пользователь базы данных, не сопоставленный ни с одним участником на уровне сервера|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Роль базы данных|Разрешение ALTER на роль, членство в роли базы данных db_securityadminfixed, членство в роли базы данных db_owner или членство в фиксированной серверной роли sysadmin.|  
|Роль приложения|Разрешение ALTER на роль, членство в предопределенной роли базы данных db_securityadmin, предопределенной роли базы данных db_owner или предопределенной роли сервера sysadmin.|  
  
 Участники, имеющие разрешение CONTROL на защищаемый объект, могут предоставлять разрешение на этот защищаемый объект.  
  
 Участники, получившие разрешение CONTROL на базу данных, такие как члены предопределенной роли базы данных db_owner, могут предоставлять любое разрешение на любой защищаемый объект в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-control-permission-on-a-user-to-another-user"></a>A. Предоставление разрешения CONTROL на пользователя другому пользователю  
 В следующем примере пользователю `CONTROL` предоставляется разрешение `AdventureWorks2012` на пользователя `Wanida` базы данных `RolandX`.  
  
```  
GRANT CONTROL ON USER::Wanida TO RolandX;  
GO  
```  
  
### <a name="b-granting-view-definition-permission-on-a-role-to-a-user-with-grant-option"></a>Б. Предоставление пользователю разрешения VIEW DEFINITION на роль с параметром GRANT OPTION  
 В следующем примере разрешение `VIEW DEFINITION` на роль `AdventureWorks2012` базы данных `SammamishParking`, с параметром `GRANT OPTION`, предоставляется пользователю этой базы данных, `JinghaoLiu`.  
  
```  
GRANT VIEW DEFINITION ON ROLE::SammamishParking   
    TO JinghaoLiu WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-impersonate-permission-on-a-user-to-an-application-role"></a>В. Предоставление роли приложения разрешения IMPERSONATE на пользователя  
 В следующем примере показано предоставление разрешения `IMPERSONATE` пользователю `HamithaL` на роль приложения `AdventureWorks2012` `AccountsPayable17`.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
```  
GRANT IMPERSONATE ON USER::HamithaL TO AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>См. также:  
 [Запрет разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения участника базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [СОЗДАТЬ РОЛЬ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [СОЗДАТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

