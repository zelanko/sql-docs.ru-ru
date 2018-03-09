---
title: "sp_changeobjectowner (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_changeobjectowner_TSQL
- sp_changeobjectowner
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changeobjectowner
ms.assetid: 45b3dc1c-1cde-45b7-a248-5195c12973e9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 00d4fbb90a767294e3d529e6fa5706eecfd841f1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spchangeobjectowner-transact-sql"></a>sp_changeobjectowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет владельца объекта в текущей базе данных.  
  
> [!IMPORTANT]  
>  Эта хранимая процедура работает только с объектами, доступными в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md) или [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) вместо него. **sp_changeobjectowner** изменяет схему и владельца. Для сохранения совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эта хранимая процедура изменит только владельцев объекта, если и текущий владелец, и новый владелец владеют схемами, которые имеют такое же имя, как и имена пользователей базы данных.  
  
> [!IMPORTANT]  
>  К этой хранимой процедуре было добавлено требование новых разрешений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changeobjectowner [ @objname = ] 'object' , [ @newowner = ] 'owner'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@objname =** ] **"***объекта***"**  
 Имя существующей таблицы, представления, определяемой пользователем функции или хранимой процедуры в текущей базе данных. *Объект* — **nvarchar(776)**, не имеет значения по умолчанию. *Объект* может быть заполнен именем владельца существующего объекта в форме *existing_owner***.** *объекта* Если схема и ее владелец имеют то же имя.  
  
 [  **@newowner=**] **"***владельца* **"**  
 Имя учетной записи безопасности, которая станет новым владельцем объекта. *владелец* — **sysname**, не имеет значения по умолчанию. *владелец* должен быть допустимым пользователем базы данных, роль сервера [!INCLUDE[msCoName](../../includes/msconame-md.md)] входа Windows или группы Windows, имеющей доступ к текущей базе данных. Если владелец является пользователем Windows или членом группы Windows, для которой нет соответствующего участника уровня базы данных, пользователь базы данных будет создан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changeobjectowner** удаляет все существующие разрешения из объекта. Придется переназначить любые разрешения, которые требуется сохранить после запуска **sp_changeobjectowner**. Таким образом, рекомендуется создать скрипт существующие разрешения, перед запуском **sp_changeobjectowner**. После изменения владения объектом можно использовать этот скрипт для переназначения разрешений. Перед тем как выполнить скрипт разрешений, в нем необходимо изменить владельца объекта.  
  
 Чтобы изменить владельца защищенного объекта, используйте инструкцию ALTER AUTHORIZATION. Чтобы изменить схему, используйте инструкцию ALTER SCHEMA.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **db_owner** предопределенной роли базы данных или членство в обоих **db_ddladmin** предопределенной роли базы данных и **db_securityadmin** предопределенной роли базы данных а также разрешение CONTROL на объект.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется владелец `authors` таблицу `Corporate\GeorgeW`.  
  
```  
EXEC sp_changeobjectowner 'authors', 'Corporate\GeorgeW';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Разрешение ALTER SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/alter-schema-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
