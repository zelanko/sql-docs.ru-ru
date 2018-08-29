---
title: sp_changeobjectowner (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_changeobjectowner_TSQL
- sp_changeobjectowner
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changeobjectowner
ms.assetid: 45b3dc1c-1cde-45b7-a248-5195c12973e9
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: e3150cce9a4ddb4fce2dd1e7bfc6196858f63ec6
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032427"
---
# <a name="spchangeobjectowner-transact-sql"></a>sp_changeobjectowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет владельца объекта в текущей базе данных.  
  
> [!IMPORTANT]  
>  Эта хранимая процедура работает только с объектами, доступными в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md) или [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) вместо этого. **sp_changeobjectowner** изменяет как схему, так и владельца. Для сохранения совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эта хранимая процедура изменит только владельцев объекта, если и текущий владелец, и новый владелец владеют схемами, которые имеют такое же имя, как и имена пользователей базы данных.  
  
> [!IMPORTANT]  
>  К этой хранимой процедуре было добавлено требование новых разрешений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changeobjectowner [ @objname = ] 'object' , [ @newowner = ] 'owner'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@objname =** ] **"***объект***"**  
 Имя существующей таблицы, представления, определяемой пользователем функции или хранимой процедуры в текущей базе данных. *Объект* — **nvarchar(776)**, не имеет значения по умолчанию. *Объект* может быть заполнен именем владельца существующего объекта в форме *existing_owner ***.*** Объект* Если схема и ее владелец имеют тем же именем.  
  
 [  **@newowner=**] **"*** владельца* **"**  
 Имя учетной записи безопасности, которая станет новым владельцем объекта. *владелец* — **sysname**, не имеет значения по умолчанию. *владелец* должен быть допустимым пользователем базы данных, роли сервера, [!INCLUDE[msCoName](../../includes/msconame-md.md)] имени входа Windows или группы Windows, имеющей доступ к текущей базе данных. Если владелец является пользователем Windows или членом группы Windows, для которой нет соответствующего участника уровня базы данных, пользователь базы данных будет создан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_changeobjectowner** удаляет все существующие разрешения из объекта. Придется переназначить любые разрешения, которые требуется сохранить после запуска **sp_changeobjectowner**. Таким образом, мы рекомендуем в скрипте существующие разрешения перед запуском **sp_changeobjectowner**. После изменения владения объектом можно использовать этот скрипт для переназначения разрешений. Перед тем как выполнить скрипт разрешений, в нем необходимо изменить владельца объекта.  
  
 Чтобы изменить владельца защищенного объекта, используйте инструкцию ALTER AUTHORIZATION. Чтобы изменить схему, используйте инструкцию ALTER SCHEMA.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **db_owner** предопределенной роли базы данных или членство в обоих **db_ddladmin** предопределенной роли базы данных и **db_securityadmin** предопределенной роли базы данных а также разрешение CONTROL на объект.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется владелец `authors` таблицу `Corporate\GeorgeW`.  
  
```  
EXEC sp_changeobjectowner 'authors', 'Corporate\GeorgeW';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER SCHEMA (Transact-SQL)](../../t-sql/statements/alter-schema-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_changedbowner (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
