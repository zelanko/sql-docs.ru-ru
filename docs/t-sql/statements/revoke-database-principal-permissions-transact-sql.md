---
title: REVOKE (разрешения на субъект базы данных)
description: Отзывает разрешения для пользователя базы данных, роли базы данных или роли приложения.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], permissions
- REVOKE statement, roles
- database user permissions [SQL Server]
- REVOKE statement, users
- application roles [SQL Server], permissions
ms.assetid: c45e1086-c25b-48bb-a764-4a893e983db2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8114ca6e50f28c4c603285affd05478c297bf881
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2020
ms.locfileid: "86485149"
---
# <a name="revoke-database-principal-permissions-transact-sql"></a>REVOKE, отмена разрешений на участника базы данных (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Отменяет разрешения, предоставленные или запрещенные для пользователя базы данных, роли базы данных или роли приложения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
       | [ ROLE :: database_role ]  
       | [ APPLICATION ROLE :: application_role ]  
    }  
    { FROM | TO } <database_principal> [ ,...n ]  
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
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *permission*  
 Указывает разрешение, которое может быть отменено у участника базы данных. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 USER ::*database_user*  
 Указывает класс и имя пользователя, у которого отменяется разрешение. Квалификатор области ( **::** ) является обязательным.  
  
 ROLE ::*database_role*  
 Указывает класс и имя роли, у которой отменяется разрешение. Квалификатор области ( **::** ) является обязательным.  
  
 APPLICATION ROLE ::*application_role*  
**Применимо к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и выше, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Указывает класс и имя роли приложения, у которой отменяется разрешение. Квалификатор области ( **::** ) является обязательным.  
  
 GRANT OPTION  
 Показывает, что отменяется право на предоставление указанного разрешения другим участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS \<database_principal> Указывает субъект, от которого субъект, выполняющий данный запрос, наследует право на отмену разрешения.  
  
 *Database_user*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
**Применимо к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и выше, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий
  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий
  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий
  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий
  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="database-user-permissions"></a>Разрешения пользователя базы данных  
 Пользователь базы данных — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно отменить у пользователя базы данных, перечислены ниже вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение пользователя базы данных|Содержится в разрешении пользователя базы данных|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>Разрешения роли базы данных  
 Роль базы данных — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно отменить у роли базы данных, перечислены ниже вместе с более общими разрешениями, неявно содержащими их.  
  
|Разрешение роли базы данных|Содержится в разрешении роли базы данных|Содержится в разрешении базы данных|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>Разрешения роли приложения  
 Роль приложения — это защищаемый объект уровня базы данных, содержащийся в базе данных, являющейся родительским элементом в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно отменить у роли приложения, перечислены ниже вместе с более общими разрешениями, неявно содержащими их.  
  
|Разрешение роли приложения|Содержится в разрешении роли приложения|Содержится в разрешении базы данных|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL для указанного участника или разрешение, неявно включающее в себя разрешение CONTROL.  
  
 Участники, получившие разрешение CONTROL для базы данных, такие как члены предопределенной роли базы данных **db_owner**, могут предоставлять любое разрешение для любого защищаемого объекта в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-revoking-control-permission-on-a-user-from-another-user"></a>A. Отмена разрешения CONTROL на пользователя у другого пользователя  
 В следующем примере у пользователя `CONTROL` отменяется разрешение [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на пользователя `Wanida` базы данных `RolandX`.  
  
```  
USE AdventureWorks2012;  
REVOKE CONTROL ON USER::Wanida FROM RolandX;  
GO  
```  
  
### <a name="b-revoking-view-definition-permission-on-a-role-from-a-user-to-which-it-was-granted-with-grant-option"></a>Б. Отмена разрешения VIEW DEFINITION на роль у пользователя, которому оно было предоставлено с параметром WITH GRANT OPTION  
 В следующем примере у пользователя `VIEW DEFINITION` отменяется разрешение [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на роль `SammamishParking` базы данных `JinghaoLiu`. Параметр `CASCADE` указан, поскольку пользователю `JinghaoLiu` было предоставлено разрешение `VIEW DEFINITION` с параметром `WITH GRANT OPTION`.  
  
```  
USE AdventureWorks2012;  
REVOKE VIEW DEFINITION ON ROLE::SammamishParking   
    FROM JinghaoLiu CASCADE;  
GO  
```  
  
### <a name="c-revoking-impersonate-permission-on-a-user-from-an-application-role"></a>В. Отмена разрешения IMPERSONATE на пользователя у роли приложения  
 В следующем примере у роли приложения `IMPERSONATE` отменяется разрешение `HamithaL` на пользователя `AccountsPayable17` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
**Применимо к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и выше, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
```  
USE AdventureWorks2012;  
REVOKE IMPERSONATE ON USER::HamithaL FROM AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на участника базы данных (Transact-SQL)](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)   
 [DENY, запрет разрешений на участника базы данных (Transact-SQL)](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ROLE (Transact-SQL)](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

