---
description: sp_adduser (Transact-SQL)
title: sp_adduser (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_adduser
- sp_adduser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adduser
ms.assetid: 61a40eb4-573f-460c-9164-bd1bbfaf8b25
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 05aa08ee4d2b518b804db93d5a2408f690b56bbc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464606"
---
# <a name="sp_adduser-transact-sql"></a>sp_adduser (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Добавляет нового пользователя в текущую базу данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adduser [ @loginame = ] 'login'   
    [ , [ @name_in_db = ] 'user' ]   
    [ , [ @grpname = ] 'role' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @loginame = ] 'login'` Имя входа или имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows. *имя входа* имеет тип **sysname**и не имеет значения по умолчанию. *имя входа* должно быть существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] именем входа или именем входа Windows.  
  
`[ @name_in_db = ] 'user'` Имя нового пользователя базы данных. *User* имеет тип **sysname**и значение по умолчанию NULL. Если *пользователь* не указан, имя новой базы данных по умолчанию принимает имя *входа* в систему. При указании параметра *пользователь* присваивает новому пользователю имя в базе данных, отличное от имени входа на уровне сервера.  
  
`[ @grpname = ] 'role'` Роль базы данных, членом которой становится новый пользователь. Аргумент *Role* имеет тип **sysname**и значение по умолчанию NULL. *роль* должна быть допустимой ролью базы данных в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 **sp_adduser** также создаст схему с именем пользователя.  
  
 После добавления пользователя следует определить разрешения, управляющие действиями, которые пользователь может выполнять, с помощью инструкций GRANT, DENY и REVOKE.  
  
 Для вывода списка допустимых имен входа используйте представление **sys. server_principals** .  
  
 Используйте **sp_helprole** для вывода списка допустимых имен ролей. При задании роли пользователь автоматически получает соответствующие этой роли разрешения. Если роль не указана, пользователь получает разрешения, предоставленные роли **Public** по умолчанию. Чтобы добавить пользователя к роли, необходимо указать значение *имени пользователя* . (*имя пользователя* может быть таким же, как *login_ID*.)  
  
 **Гостевая** учетная запись пользователя уже существует в каждой базе данных. Добавление **гостевого** пользователя включит этого пользователя, если он был ранее отключен. По умолчанию **Гостевая** учетная запись пользователя отключена в новых базах данных.  
  
 **sp_adduser** не может выполняться внутри определяемой пользователем транзакции.  
  
 Вы не можете добавить **гостевого** пользователя, так как **гостевой** пользователь уже существует в каждой базе данных. Чтобы включить **гостевой** пользователь, предоставьте ему разрешение **Guest** Connect, как показано ниже.  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо, чтобы пользователь был владельцем базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-database-user"></a>A. Добавление пользователя базы данных  
 В следующем примере пользователь `Vidur` добавляется в существующую роль `Recruiting` текущей базы данных с помощью существующего имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`Vidur`.  
  
```  
EXEC sp_adduser 'Vidur', 'Vidur', 'Recruiting';  
```  
  
### <a name="b-adding-a-database-user-with-the-same-login-id"></a>Б. Добавление пользователя базы данных с таким же идентификатором входа  
 В приведенном ниже примере пользователь `Arvind` добавляется в текущую базу данных для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`Arvind`. Этот пользователь принадлежит к роли **Public** по умолчанию.  
  
```  
EXEC sp_adduser 'Arvind';  
```  
  
### <a name="c-adding-a-database-user-with-a-different-name-than-its-server-level-login"></a>В. Добавление пользователя базы данных с именем, отличным от имени входа уровня сервера  
 В приведенном ниже примере в текущую базу данных, в которой есть пользователь с именем `BjornR`, добавляется имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`Bjorn`, а также пользователь `Bjorn` добавляется в роль `Production`.  
  
```  
EXEC sp_adduser 'BjornR', 'Bjorn', 'Production';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
