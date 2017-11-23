---
title: "ALTER APPLICATION ROLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_APPLICATION_ROLE_TSQL
- ALTER APPLICATION ROLE
dev_langs: TSQL
helpviewer_keywords:
- modifying application roles
- passwords [SQL Server], application roles
- ALTER APPLICATION ROLE statement
- application roles [SQL Server], modifying
ms.assetid: c6cd5d0f-18f4-49be-b161-64d9c5569086
caps.latest.revision: "46"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 551e20391cb035cd41eb400e4877fe162d241608
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="alter-application-role-transact-sql"></a>ALTER APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет имя, пароль или схему по умолчанию для роли приложения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER APPLICATION ROLE application_role_name   
    WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
    NAME = new_application_role_name   
    | PASSWORD = 'password'  
    | DEFAULT_SCHEMA = schema_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *application_role_name*  
 Имя изменяемой роли приложения.  
  
 ИМЯ =*new_application_role_name*  
 Указывает новое имя роли приложения. Это имя не должно быть уже занято для обращения к любому из участников базы данных.  
  
 ПАРОЛЬ = "*пароль*"  
 Указывает пароль для роли приложения. *пароль* должен соответствовать требованиям политики паролей Windows компьютера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Всегда используйте надежные пароли.  
  
 Значение DEFAULT_SCHEMA =*schema_name*  
 Задает первую схему для поиска сервером, когда он разрешает имена объектов. *schema_name* может быть схемой, не существует в базе данных.  
  
## <a name="remarks"></a>Замечания  
 Если новое имя роли приложения уже существует в базе данных, инструкция завершится неудачно. Если изменяется имя роли приложения, пароль или схема по умолчанию, то идентификатор, связанный с этой ролью, не изменяется.  
  
> [!IMPORTANT]  
>  Политика истечения срока действия пароля не применяется к паролям роли приложения. По этой причине позаботьтесь о выборе сильных паролей. Приложения, которые используют роли приложения, должны хранить свои пароли.  
  
 Роли приложения можно просмотреть в представлении каталога sys.database_principals.  
  
> [!CAUTION]  
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]поведение схем отличается от поведения в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Код, предполагающий, что схемы эквивалентны пользователям базы данных, может возвращать неверные результаты. Старые представления каталога, включая sysobjects, не следует использовать в базе данных, в каком-либо из следующих инструкций DDL инструкций была выполнена: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. В базе данных, в которой когда-либо выполнялась любая из этих инструкций, необходимо использовать новые представления каталога. Новые представления каталога принимают во внимание разделение участников и схем, которые представлены в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Дополнительные сведения о представлениях каталогов см. в статье [Представления системных каталогов (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо наличие разрешения ALTER ANY APPLICATION ROLE для этой базы данных. Чтобы изменить схему по умолчанию, пользователь должен иметь разрешение ALTER на роль приложения. Роль приложения может менять свою схему по умолчанию, но не имя или пароль.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-name-of-application-role"></a>A. Изменение имени роли приложения  
 В следующем примере изменяется имя роли приложения `weekly_receipts` на `receipts_ledger`.  
  
```  
USE AdventureWorks2012;  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987Gbv8$76sPYY5m23' ,   
    DEFAULT_SCHEMA = Sales;  
GO  
ALTER APPLICATION ROLE weekly_receipts   
    WITH NAME = receipts_ledger;  
GO  
```  
  
### <a name="b-changing-the-password-of-application-role"></a>Б. Изменение пароля роли приложения  
 В следующем примере изменяется пароль роли приложения `receipts_ledger`.  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH PASSWORD = '897yUUbv867y$200nk2i';  
GO  
```  
  
### <a name="c-changing-the-name-password-and-default-schema"></a>В. Изменение имени, пароля и схемы по умолчанию  
 В следующем примере одновременно изменяется имя, пароль и схема по умолчанию для роли приложения `receipts_ledger`.  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH NAME = weekly_ledger,   
    PASSWORD = '897yUUbv77bsrEE00nk2i',   
    DEFAULT_SCHEMA = Production;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Роли приложений](../../relational-databases/security/authentication-access/application-roles.md)   
 [СОЗДАТЬ РОЛЬ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Удаление РОЛИ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
