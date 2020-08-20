---
description: sp_changeobjectowner (Transact-SQL)
title: sp_changeobjectowner (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
ms.openlocfilehash: e96c93be7b21deb0966e0a48f5fde3258501ac6c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464432"
---
# <a name="sp_changeobjectowner-transact-sql"></a>sp_changeobjectowner (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет владельца объекта в текущей базе данных.  
  
> [!IMPORTANT]
>  Эта хранимая процедура работает только с объектами, доступными в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] . [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте [ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md) или [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) . **sp_changeobjectowner** изменяет как схему, так и владельца. Для сохранения совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эта хранимая процедура изменит только владельцев объекта, если и текущий владелец, и новый владелец владеют схемами, которые имеют такое же имя, как и имена пользователей базы данных.  
> 
> [!IMPORTANT]
>  К этой хранимой процедуре было добавлено требование новых разрешений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changeobjectowner [ @objname = ] 'object' , [ @newowner = ] 'owner'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'object'` Имя существующей таблицы, представления, определяемой пользователем функции или хранимой процедуры в текущей базе данных. *объект* имеет тип **nvarchar (776)** и не имеет значения по умолчанию. *объект* можно уточнить с помощью владельца существующего объекта в форме _existing_owner_**.** _объект_ , если схема и ее владелец имеют одинаковые имена.  
  
`[ @newowner = ] 'owner_ '` Имя учетной записи безопасности, которая будет новым владельцем объекта. Аргумент *owner* имеет тип **sysname**и не имеет значения по умолчанию. *владельцем* должен быть допустимый пользователь базы данных, роль сервера, [!INCLUDE[msCoName](../../includes/msconame-md.md)] имя входа Windows или группа Windows с доступом к текущей базе данных. Если владелец является пользователем Windows или членом группы Windows, для которой нет соответствующего участника уровня базы данных, пользователь базы данных будет создан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 **sp_changeobjectowner** удаляет все существующие разрешения из объекта. Вам потребуется повторно применить все разрешения, которые вы хотите сохранить после выполнения **sp_changeobjectowner**. Поэтому перед запуском **sp_changeobjectowner**рекомендуется создать скрипты для существующих разрешений. После изменения владения объектом можно использовать этот скрипт для переназначения разрешений. Перед тем как выполнить скрипт разрешений, в нем необходимо изменить владельца объекта.  
  
 Чтобы изменить владельца защищенного объекта, используйте инструкцию ALTER AUTHORIZATION. Чтобы изменить схему, используйте инструкцию ALTER SCHEMA.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** или членство в предопределенной роли базы данных **db_ddladmin** и **db_securityadmin** предопределенной роли базы данных, а также разрешение CONTROL на объект.  
  
## <a name="examples"></a>Примеры  
 В следующем примере владелец `authors` таблицы изменяется на `Corporate\GeorgeW` .  
  
```  
EXEC sp_changeobjectowner 'authors', 'Corporate\GeorgeW';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SCHEMA (Transact-SQL)](../../t-sql/statements/alter-schema-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_changedbowner (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
