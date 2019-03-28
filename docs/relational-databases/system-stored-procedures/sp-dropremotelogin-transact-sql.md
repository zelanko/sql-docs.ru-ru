---
title: sp_dropremotelogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropremotelogin
- sp_dropremotelogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropremotelogin
ms.assetid: 9f097652-a286-40b2-be73-568d77ada698
ms.author: vanto
manager: craigg
ms.openlocfilehash: 910f4f02c17ba0f6524648b9ac1eb201d735b238
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527926"
---
# <a name="spdropremotelogin-transact-sql"></a>sp_dropremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет отображение удаленного имени входа на локальное имя входа, используемое для выполнения хранимых процедур удаленно, а не на локальном сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Используйте вместо него связанные серверы и хранимые процедуры связанных серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @remoteserver = ] 'remoteserver'` — Имя удаленного сервера, сопоставленного для удаленного имени входа, который должен быть удален. *удаленный сервер* — **sysname**, не имеет значения по умолчанию. *удаленный сервер* должен уже существовать.  
  
`[ @loginame = ] 'login'` — Это необязательное имя входа на локальном сервере, который связан с удаленным сервером. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. *Имя входа* должен уже существовать, если задано.  
  
`[ @remotename = ] 'remote_name'` Необязательное имя удаленного имени входа, которое сопоставляется с *входа* при входе в систему с удаленного сервера. *remote_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если только *remoteserver* указан, все удаленные имена входа для этих удаленных серверов удаляются с локального сервера. Если *входа* также будет указан, все удаленные имена входа из *remoteserver* отображенные на это заданное локальное имя входа, удаляются с локального сервера. Если *remote_name* также указан только удаленное имя входа для этого удаленного пользователя с *remoteserver* удаляется с локального сервера.  
  
 Чтобы добавить пользователей локального сервера, используйте **sp_addlogin**. Для удаления пользователей локального сервера, используйте **sp_droplogin**.  
  
 Удаленные имена входа требуются только в тех случаях, когда используются ранние версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 и более поздних вместо них используются имена входа связанных серверов. Используйте **sp_addlinkedsrvlogin** и **sp_droplinkedsrvlogin** для добавления и удаления имен входа связанного сервера.  
  
 **sp_dropremotelogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** или **securityadmin** предопределенных ролей сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-all-remote-logins-for-a-remote-server"></a>A. Удаление всех удаленных имен входа с удаленного сервера  
 Следующий пример удаляет вхождение для удаленного сервера `ACCOUNTS` и поэтому удаляет все сопоставления между именами входа на локальном сервере и удаленными именами входа на удаленном сервере.  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-dropping-a-login-mapping"></a>Б. Удаление сопоставления имени входа  
 Следующий пример удаляет сопоставление удаленных имен входа с удаленного сервера `ACCOUNTS` на локальное имя входа `Albert`.  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-dropping-a-remote-user"></a>В. Удаление удаленного пользователя  
 Следующий пример удаляет имя входа `Chris` на удаленном сервере `ACCOUNTS`, которое сопоставлено локальному имени входа `salesmgr`.  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
