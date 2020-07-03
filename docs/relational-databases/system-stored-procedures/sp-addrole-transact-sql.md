---
title: sp_addrole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrole
- sp_addrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrole
ms.assetid: e8a21642-8440-419a-8585-93d3d9d44f00
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f364de4eb2760c5beeae17360fb84ffd52fd7181
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85876737"
---
# <a name="sp_addrole-transact-sql"></a>sp_addrole (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Создает новую роль базы данных в текущей базе данных.  
  
> [!IMPORTANT]
>  **sp_addrole** входит в совместимость с предыдущими версиями [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и может не поддерживаться в будущем выпуске. Вместо этого используйте [CREATE ROLE](../../t-sql/statements/create-role-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'`Имя новой роли базы данных. *Role* имеет тип **sysname**и не имеет значения по умолчанию. *роль* должна быть допустимым идентификатором (ID) и не должна существовать в текущей базе данных.  
  
`[ @ownername = ] 'owner'`Владелец новой роли базы данных. *owner* имеет тип **sysname**и значение по умолчанию текущего выполняемого пользователя. *владелец* должен быть пользователем базы данных или ролью базы данных в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 Имена ролей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать от 1 до 128 символов, включая буквы, символы и цифры. Имена ролей базы данных не могут: содержать обратную косую черту ( \\ ), иметь значение null или пустую строку (**""**).  
  
 После добавления роли базы данных используйте [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) , чтобы добавить участников в роль. При использовании инструкций GRANT, DENY или REVOKE для назначения разрешений роли базы данных члены данной роли наследуют эти разрешения, как если бы они были применены напрямую к их учетным записям.  
  
> [!NOTE]  
>  Новые роли сервера создавать нельзя. Роли можно создавать только на уровне базы данных.  
  
 **sp_addrole** нельзя использовать внутри определяемой пользователем транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо наличие разрешения CREATE ROLE в базе данных. При создании схемы необходимо наличие разрешения CREATE SCHEMA в этой базе данных. Если *владелец* указан как пользователь или группа, необходимо выполнить олицетворение для этого пользователя или группы. Если *владелец* указан как роль, необходимо разрешение ALTER на эту роль или член этой роли. Если владелец указан как роль приложения, то для этой роли приложения необходимо разрешение ALTER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере в текущую базу данных добавляется новая роль с именем `Managers`.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
