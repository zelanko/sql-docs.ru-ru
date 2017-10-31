---
title: "Разрешения типа GRANT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
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
- permissions [SQL Server], types
- granting permissions [SQL Server], types
- GRANT statement, types
- type permissions [SQL Server]
ms.assetid: 14bd2fb3-1446-49c0-be87-c6a670317ed0
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e29ede5580418d1cbcb55d5a877196c3cabab92
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grant-type-permissions-transact-sql"></a>GRANT, предоставление разрешений на тип (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Предоставляет разрешения на тип.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GRANT permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
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
 Указывает разрешение, которое может быть предоставлено на тип. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 В ТИПЕ **::** [ *имя_схемы***.** ] *type_name*  
 Указывает тип, на который выдается разрешение. Квалификатор области (**::**) является обязательным. Если *schema_name* не указан, используется схема по умолчанию. Если *имя_схемы* указана, указание квалификатора области схемы (**.**) является обязательным.  
  
 Чтобы \<database_principal > Указывает участника, к которому предоставляется разрешение.  
  
 WITH GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
 AS \<database_principal > Указывает участника, от которого участник, выполняющий данный запрос, наследует право предоставления разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
 Тип — это защищаемый объект уровня схемы; он содержится в схеме, являющейся его родителем в иерархии разрешений.  
  
> [!IMPORTANT]  
>  **Предоставление**, **DENY,** и **ОТОЗВАТЬ** разрешения не применяются к системным типам. Определяемым пользователем типам можно предоставлять разрешения. Дополнительные сведения об определяемых пользователем типах см. в разделе [работа с определяемые пользователем типы в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md).  
  
 Наиболее специфичные и ограниченные разрешения, которые можно предоставлять на тип, перечислены в следующей таблице вместе с более общими разрешениями, неявно содержащими их.  
  
|Разрешение типа|Содержится в разрешении типа данных|Содержится в разрешении схемы|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|Выполните|CONTROL|Выполните|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое.  
  
 При использовании параметра AS налагаются следующие дополнительные требования.  
  
|AS|Необходимо дополнительное разрешение|  
|--------|------------------------------------|  
|Пользователь базы данных|Разрешение IMPERSONATE для пользователя, членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin** предопределенной роли сервера.|  
|Пользователь базы данных, сопоставленный имени входа Windows|Разрешение IMPERSONATE для пользователя, членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin** предопределенной роли сервера.|  
|Пользователь базы данных, сопоставленный группе Windows|Членство в группе Windows, членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin**предопределенной роли сервера.|  
|Пользователь базы данных, сопоставленный сертификату|Членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin** предопределенной роли сервера.|  
|Пользователь базы данных, сопоставленный асимметричному ключу|Членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin** предопределенной роли сервера.|  
|Пользователь базы данных, не сопоставленный ни с одним участником на уровне сервера|Разрешение IMPERSONATE для пользователя, членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin** предопределенной роли сервера.|  
|Роль базы данных|Разрешение ALTER для роли, членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin**предопределенной роли сервера.|  
|Роль приложения|Разрешение ALTER для роли, членство в **db_securityadmin** предопределенной роли базы данных, членство в **db_owner** предопределенной роли базы данных или членство в **sysadmin**предопределенной роли сервера.|  
  
## <a name="examples"></a>Примеры  
 В следующем примере предоставляется разрешение `VIEW DEFINITION` на столбец `GRANT OPTION` пользователю `PhoneNumber` с параметром `KhalidR`. `PhoneNumber` расположен в схеме `Telemarketing`.  
  
```  
GRANT VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Запрет разрешения типа &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [Разрешения типа REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


