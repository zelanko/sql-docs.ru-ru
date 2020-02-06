---
title: CREATE APPLICATION ROLE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- APPLICATION_ROLE_TSQL
- CREATE APPLICATION ROLE
- sql13.swb.applicationrole.permissions.f1
- APPLICATION
- APPLICATION ROLE
- CREATE_APPLICATION_ROLE_TSQL
- APPLICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE APPLICATION ROLE statement
- application roles [SQL Server], creating
ms.assetid: 647386da-ee80-41cf-86c9-dd590f9d66b6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dc3caf4c1643405cc7db31e2a9c76cf70456b272
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73064592"
---
# <a name="create-application-role-transact-sql"></a>CREATE APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Добавляет роль приложения к текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE APPLICATION ROLE application_role_name   
    WITH PASSWORD = 'password' [ , DEFAULT_SCHEMA = schema_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *application_role_name*  
 Указывает имя роли приложения. Это имя не должно быть уже занято для обращения к любому из участников базы данных.  
  
 PASSWORD **='** _password_ **'**  
 Указывает пароль для включения роли приложения пользователями базы данных. Всегда используйте надежные пароли. *password* должен соответствовать требованиям политики паролей Windows применительно к компьютеру, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 DEFAULT_SCHEMA **=** _schema\_name_  
 Указывает первую схему, в которой сервер будет производить поиск при распознавании имен объектов для этой роли. Если значение DEFAULT_SCHEMA не заполнено, роль приложения будет использовать в качестве схемы по умолчанию DBO. Аргумент *schema_name* может быть схемой, которой нет в базе данных.  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]  
>  Сложность пароля проверяется при установке паролей для роли приложения. Приложения, которые используют роли приложения, должны хранить свои пароли. Пароли ролей приложения всегда должны храниться в зашифрованном виде.  
  
 Роли приложения можно просмотреть в представлении каталога [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
 Сведения об использовании ролей приложения см. в разделе [Роли приложений](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Разрешения  
 Необходимо наличие разрешения ALTER ANY APPLICATION ROLE для этой базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается роль приложения с именем `weekly_receipts`, паролем `987Gbv876sPYY5m23` и схемой по умолчанию `Sales`.  
  
```sql  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987G^bv876sPY)Y5m23'   
    , DEFAULT_SCHEMA = Sales;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Роли приложений](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_setapprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [ALTER APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [Политика паролей](../../relational-databases/security/password-policy.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
