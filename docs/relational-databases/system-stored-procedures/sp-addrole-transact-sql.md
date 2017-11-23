---
title: "sp_addrole (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_addrole
- sp_addrole_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_addrole
ms.assetid: e8a21642-8440-419a-8585-93d3d9d44f00
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0fa5ac729746e984ae958628a808158f389a58f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spaddrole-transact-sql"></a>sp_addrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новую роль базы данных в текущей базе данных.  
  
> [!IMPORTANT]  
>  **sp_addrole** включен для обеспечения совместимости с более ранними версиями [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и может не поддерживаться в будущих выпусках. Используйте [CREATE ROLE](../../t-sql/statements/create-role-transact-sql.md) вместо него.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rolename =** ] **"***роли***"**  
 Имя новой роли базы данных. *роль* — **sysname**, не имеет значения по умолчанию. *роль* должен быть допустимым идентификатором (ID) и не должен существовать в текущей базе данных.  
  
 [  **@ownername =**] **"***владельца***"**  
 Владелец новой роли базы данных. *владелец* — **sysname**, значение по умолчанию — текущий пользователь. *владелец* должен быть пользователем базы данных или роли базы данных в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Имена ролей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать от 1 до 128 символов, включая буквы, символы и цифры. Имена ролей базы данных не могут: содержать обратную косую черту (\\), иметь значение NULL, или пустой строкой (**''**).  
  
 После добавления роли базы данных, используйте [sp_addrolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) Добавление участников к роли. При использовании инструкций GRANT, DENY или REVOKE для назначения разрешений роли базы данных члены данной роли наследуют эти разрешения, как если бы они были применены напрямую к их учетным записям.  
  
> [!NOTE]  
>  Новые роли сервера создавать нельзя. Роли можно создавать только на уровне базы данных.  
  
 **sp_addrole** нельзя использовать внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Permissions  
 Необходимо наличие разрешения CREATE ROLE в базе данных. При создании схемы необходимо наличие разрешения CREATE SCHEMA в этой базе данных. Если *владельца* указан как пользователь или группа, требует разрешения IMPERSONATE на этого пользователя или группу. Если *владельца* указан как роль, необходимо разрешение ALTER для этой роли или члена этой роли. Если владелец указан как роль приложения, то для этой роли приложения необходимо разрешение ALTER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере в текущую базу данных добавляется новая роль с именем `Managers`.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
