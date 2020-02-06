---
title: GRANT, предоставление разрешений для типа (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], types
- granting permissions [SQL Server], types
- GRANT statement, types
- type permissions [SQL Server]
ms.assetid: 14bd2fb3-1446-49c0-be87-c6a670317ed0
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7695fda9dd287239f4ef88ea5c279e11a0b5abdd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73982501"
---
# <a name="grant-type-permissions-transact-sql"></a>GRANT, предоставление разрешений на тип (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
 *permission*  
 Указывает разрешение, которое может быть предоставлено на тип. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON TYPE **::** [ _schema_name_ **.** ] *type_name*  
 Указывает тип, на который выдается разрешение. Квалификатор области ( **::** ) является обязательным. Если не указан аргумент *schema_name*, подразумевается схема по умолчанию. Если указан аргумент *schema_name*, обязательно указание квалификатора области схемы ( **.** ).  
  
 TO \<database_principal> указывает субъект, которому предоставляется разрешение.  
  
 WITH GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
 AS \<database_principal> указывает участника, от которого участник, выполняющий данный запрос, наследует право на предоставление разрешения.  
  
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
 Тип — это защищаемый объект уровня схемы; он содержится в схеме, являющейся его родителем в иерархии разрешений.  
  
> [!IMPORTANT]  
>  Разрешения **GRANT**, **DENY** и **REVOKE** не применяются к системным типам. Определяемым пользователем типам можно предоставлять разрешения. Дополнительные сведения об определяемых пользователем типах см. в разделе [Работа с определяемыми пользователем типами в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md).  
  
 Наиболее специфичные и ограниченные разрешения, которые можно предоставлять на тип, перечислены в следующей таблице вместе с более общими разрешениями, неявно содержащими их.  
  
|Разрешение типа|Содержится в разрешении типа данных|Содержится в разрешении схемы|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|EXECUTE|CONTROL|EXECUTE|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое.  
  
 При использовании параметра AS налагаются следующие дополнительные требования.  
  
|AS|Необходимо дополнительное разрешение|  
|--------|------------------------------------|  
|пользователь базы данных;|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|пользователь базы данных, сопоставленный с именем входа Windows;|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|пользователь базы данных, сопоставленный с группой Windows;|Членство в группе Windows, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|пользователь базы данных, сопоставленный с сертификатом;|Членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|пользователь базы данных, сопоставленный с асимметричным ключом;|Членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|Пользователь базы данных, не сопоставленный ни с одним участником на уровне сервера|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных **db_securityadmin**, членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли сервера **sysadmin**.|  
|роль базы данных;|Разрешение ALTER на роль, членство в предопределенной роли базы данных **db_securityadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли сервера **sysadmin**.|  
|Роль приложения|Разрешение ALTER на роль, членство в предопределенной роли базы данных **db_securityadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли сервера **sysadmin**.|  
  
## <a name="examples"></a>Примеры  
 В следующем примере предоставляется разрешение `VIEW DEFINITION` с аргументом `GRANT OPTION` для определенного пользователем типа `PhoneNumber` пользователю `KhalidR`. `PhoneNumber` расположен в схеме `Telemarketing`.  
  
```  
GRANT VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [DENY, запрет разрешений на тип (Transact-SQL)](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на тип (Transact-SQL)](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

