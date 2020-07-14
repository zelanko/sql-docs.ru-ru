---
title: REVOKE, отмена разрешения на тип (Transact-SQL) | Документы Майкрософт
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
- REVOKE statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
ms.assetid: 3969c7e9-ca10-4c67-971b-25d2dfccf650
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3cd5a1b5404728dde5f72928111391e13842fe35
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735338"
---
# <a name="revoke-type-permissions-transact-sql"></a>REVOKE, отмена разрешения на тип (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Отменяет разрешения на использование типа.  
  
  ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]   
    ON TYPE :: [ schema_name ]. type_name   
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
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Разрешение на работу с типом, которое можно отменить. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON TYPE **::** [ *schema_name* ] **.** *type_name*  
 Тип, разрешение на работу с которым отменяется. Квалификатор области ( **::** ) является обязательным. Если не указан аргумент *schema_name*, подразумевается схема по умолчанию. Если указан аргумент *schema_name*, обязательно указание квалификатора области схемы ( **.** ).  
  
 { FROM | TO } \<database_principal> Задает субъект, у которого отменяется разрешение.  
  
 GRANT OPTION  
 Показывает, что отменяется право на предоставление указанного разрешения другим участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS \<database_principal> Указывает субъект, от которого субъект, выполняющий данный запрос, получает право на отмену разрешения.  
  
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
  
 Самые специфичные и ограниченные разрешения на работу с типом, которые можно отменить, приведены в следующей таблице вместе с общими разрешениями, неявно их охватывающими.  
  
|Разрешение типа|Содержится в разрешении типа данных|Содержится в разрешении схемы|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|EXECUTE|CONTROL|EXECUTE|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Для данного типа требуется разрешение CONTROL. Если используется предложение AS, заданный участник должен быть владельцем типа.  
  
## <a name="examples"></a>Примеры  
 Следующий код отменяет разрешение `VIEW DEFINITION`, связанное с пользовательским типом `PhoneNumber`, для пользователя `KhalidR`. Параметр `CASCADE` показывает, что разрешение `VIEW DEFINITION` будет также отменено для участников, которым предоставил это разрешение `KhalidR`. `PhoneNumber` расположен в схеме `Telemarketing`.  
  
```  
REVOKE VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    FROM KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на тип (Transact-SQL)](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [DENY, запрет разрешений на тип (Transact-SQL)](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Защищаемые объекты](../../relational-databases/security/securables.md)  
  
  

