---
title: DENY, запрет разрешений на тип (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- DENY statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
- denying permissions [SQL Server], types
ms.assetid: 564e3500-c567-43dc-993b-9ab50e99cf3f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5be985468ab82dfbe08e6ab02b127e383a1b39c2
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2020
ms.locfileid: "86484775"
---
# <a name="deny-type-permissions-transact-sql"></a>DENY, запрет разрешений на тип (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Отказывает в разрешениях на тип в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DENY permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
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
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *permission*  
 Обозначает разрешение, которое можно запретить для типа. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON TYPE **::** [ _schema_name_ **.** ] *type_name*  
 Задает тип, для которого запрещается разрешение. Квалификатор области ( **::** ) является обязательным. Если не указан аргумент *schema_name*, подразумевается схема по умолчанию. Если указан аргумент *schema_name*, обязательно указание квалификатора области схемы ( **.** ).  
  
 TO \<database_principal>  
 Задает участника, для которого запрещается разрешение.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS \<database_principal>  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения.  
  
 *Database_user*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
   
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
 Тип — это защищаемый объект уровня схемы; он содержится в схеме, являющейся его родителем в иерархии разрешений.  
  
> [!IMPORTANT]  
>  Разрешения **GRANT**, **DENY** и **REVOKE** не применяются к системным типам. Определяемым пользователем типам можно предоставлять разрешения. Дополнительные сведения об определяемых пользователем типах см. в разделе [Работа с определяемыми пользователем типами в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md).  
  
 Наиболее специфичные и ограниченные разрешения, которые можно запретить для типа, перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение типа|Содержится в разрешении типа данных|Содержится в разрешении схемы|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|EXECUTE|CONTROL|EXECUTE|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Для данного типа требуется разрешение CONTROL. При использовании предложения AS указанный участник должен быть владельцем типа запрещаемого разрешения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере разрешение `VIEW DEFINITION` на столбец `CASCADE` запрещается для пользователя `PhoneNumber` с параметром `KhalidR`. `PhoneNumber` расположен в схеме `Telemarketing`.  
  
```  
DENY VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на тип (Transact-SQL)](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на тип (Transact-SQL)](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Защищаемые объекты](../../relational-databases/security/securables.md)  
  
  
