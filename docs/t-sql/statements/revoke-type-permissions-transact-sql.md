---
title: "Отмена разрешений на тип (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- REVOKE statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
ms.assetid: 3969c7e9-ca10-4c67-971b-25d2dfccf650
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3de9121b53223ed03a2c3858fe7279cfb52af89
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-type-permissions-transact-sql"></a>REVOKE, отмена разрешения на тип (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отменяет разрешения на использование типа.  
  
  ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 *разрешение*  
 Разрешение на работу с типом, которое можно отменить. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 В ТИПЕ **::** [ *имя_схемы* ] **.** *Функция TYPE_NAME*  
 Тип, разрешение на работу с которым отменяется. Квалификатор области (**::**) является обязательным. Если *schema_name* не указан, используется схема по умолчанию. Если *имя_схемы* указана, указание квалификатора области схемы (**.**) является обязательным.  
  
 {ИЗ | К} \<database_principal > Указывает участника, от которого отменяется разрешение.  
  
 GRANT OPTION  
 Показывает, что отменяется право на предоставление указанного разрешения другим участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS \<database_principal > Указывает участника, от которого участник, выполняющий данный запрос, наследует право отмены разрешения.  
  
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
  
 Самые специфичные и ограниченные разрешения на работу с типом, которые можно отменить, приведены в следующей таблице вместе с общими разрешениями, неявно их охватывающими.  
  
|Разрешение типа|Содержится в разрешении типа данных|Содержится в разрешении схемы|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|Выполните|CONTROL|Выполните|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Для данного типа требуется разрешение CONTROL. Если используется предложение AS, заданный участник должен быть владельцем типа.  
  
## <a name="examples"></a>Примеры  
 Следующий код отменяет разрешение `VIEW DEFINITION`, связанное с пользовательским типом `PhoneNumber`, для пользователя `KhalidR`. Параметр `CASCADE` показывает, что разрешение `VIEW DEFINITION` будет также отменено для участников, которым предоставил это разрешение `KhalidR`. `PhoneNumber` расположен в схеме `Telemarketing`.  
  
```  
REVOKE VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    FROM KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Разрешения типа GRANT &#40; Transact-SQL &#41;](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [Запрет разрешения типа &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Защищаемые объекты](../../relational-databases/security/securables.md)  
  
  

