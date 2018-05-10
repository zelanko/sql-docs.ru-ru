---
title: DENY, отказ в разрешениях на уровне субъекта базы данных (Transact-SQL) | Документы Майкрософт
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
- database roles [SQL Server], permissions
- denying permissions [SQL Server], database roles
- denying permissions [SQL Server], database users
- permissions [SQL Server], database roles
- DENY statement, database roles
- database user permissions [SQL Server]
- permissions [SQL Server], application roles
- permissions [SQL Server], database users
- database permissions [SQL Server], denying
- DENY statement, application roles
- DENY statement, database users
- denying permissions [SQL Server], application roles
- application roles [SQL Server], permissions
ms.assetid: e2429a5d-e9be-4c05-be20-414d1038a63a
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c1ad7d85472fe253dc507f34f225130b8d7beaf7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="deny-database-principal-permissions-transact-sql"></a>DENY, запрет разрешений на участника базы данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения, предоставленные пользователю базы данных, роли базы данных или роли приложения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
     | [ ROLE :: database_role ]  
     | [ APPLICATION ROLE :: application_role ]  
    }  
    TO <database_principal> [ ,...n ]  
      [ CASCADE ]  
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
 *permission*  
 Обозначает разрешение, которое можно запретить для участника базы данных. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 USER ::*database_user*  
 Указывает класс и имя пользователя, для которых запрещается разрешение. Квалификатор области (**::**) является обязательным.  
  
 ROLE ::*database_role*  
 Указывает класс и имя роли, для которой запрещается разрешение. Квалификатор области (**::**) является обязательным.  
  
 APPLICATION ROLE ::*application_role*  
 **Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Указывает класс и имя роли приложения, для которой запрещается разрешение. Квалификатор области (**::**) является обязательным.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS \<database_principal>  
 Указывает участника, от которого участник, выполняющий данный запрос, получает право на отмену разрешения.  
  
 *Database_user*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
 **Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
  Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
  Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="database-user-permissions"></a>Разрешения пользователя базы данных  
 Пользователь базы данных — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить для пользователя базы данных, перечислены в следующей таблице наряду с общими разрешениями, неявно их содержащими.  
  
|Разрешение пользователя базы данных|Содержится в разрешении пользователя базы данных|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>Разрешения роли базы данных  
 Роль базы данных — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить для роли базы данных, перечислены в следующей таблице наряду с общими разрешениями, неявно их содержащими.  
  
|Разрешение роли базы данных|Содержится в разрешении роли базы данных|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>Разрешения роли приложения  
 Роль приложения — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить для роли приложения, перечислены в следующей таблице наряду с общими разрешениями, неявно их содержащими.  
  
|Разрешение роли приложения|Содержится в разрешении роли приложения|Содержится в разрешении базы данных|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL для указанного участника или разрешение, неявно включающее в себя разрешение CONTROL.  
  
 Объекты, получившие разрешение CONTROL для базы данных, такие как члены предопределенной роли базы данных db_owner, могут запрещать любое разрешение для любого защищаемого объекта базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-denying-control-permission-on-a-user-to-another-user"></a>A. Запрет разрешения CONTROL на одного пользователя другому  
 Следующий пример отклоняет разрешение `CONTROL` от пользователя `Wanida` базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] к пользователю `RolandX`.  
  
```  
USE AdventureWorks2012;  
DENY CONTROL ON USER::Wanida TO RolandX;  
GO  
```  
  
### <a name="b-denying-view-definition-permission-on-a-role-to-a-user-to-which-it-was-granted-with-grant-option"></a>Б. Запрет разрешения VIEW DEFINITION на роль пользователю, которому оно было предоставлено параметром GRANT OPTION  
 Следующий пример запрещает разрешение `VIEW DEFINITION` для роли `SammamishParking` базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] пользователю базы данных `JinghaoLiu`. Используется параметр `CASCADE`, поскольку пользователю `JinghaoLiu` было предоставлено разрешение VIEW DEFINITION параметром WITH GRANT OPTION.  
  
```  
USE AdventureWorks2012;  
DENY VIEW DEFINITION ON ROLE::SammamishParking   
    TO JinghaoLiu CASCADE;  
GO  
```  
  
### <a name="c-denying-impersonate-permission-on-a-user-to-an-application-role"></a>В. Запрет разрешения IMPERSONATE на пользователя роли приложения  
 В следующем примере показано, как отменить разрешение `IMPERSONATE` пользователю `HamithaL` на роль приложения [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] `AccountsPayable17`.  
  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
```  
USE AdventureWorks2012;  
DENY IMPERSONATE ON USER::HamithaL TO AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на участника базы данных (Transact-SQL)](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на субъекта базы данных (Transact-SQL)](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ROLE (Transact-SQL)](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
