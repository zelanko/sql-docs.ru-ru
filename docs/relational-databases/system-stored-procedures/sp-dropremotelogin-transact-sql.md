---
title: "sp_dropremotelogin (Transact-SQL) | Документы Microsoft"
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
- sp_dropremotelogin
- sp_dropremotelogin_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_dropremotelogin
ms.assetid: 9f097652-a286-40b2-be73-568d77ada698
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9edb5db6819950e517f26bee0d144ef3cf567bc
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
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
 [  **@remoteserver =** ] **"***remoteserver***"**  
 Имя удаленного сервера, сопоставленного с удаляемым именем входа. *удаленный сервер* — **sysname**, не имеет значения по умолчанию. *удаленный сервер* должен уже существовать.  
  
 [  **@loginame =** ] **"***входа***"**  
 Необязательное имя входа на локальном сервере, которое связано с удаленным сервером. *Имя входа* — **sysname**, значение по умолчанию NULL. *Имя входа* должен уже существовать, если задан.  
  
 [  **@remotename =** ] **"***remote_name***"**  
 Необязательное имя удаленного имени входа, сопоставленного *входа* при входе в систему с удаленного сервера. *remote_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Если только *remoteserver* указан, все удаленные имена входа для этих удаленных серверов удаляются с локального сервера. Если *входа* также является, то все удаленные имена входа из *remoteserver* отображенные на это заданное локальное имя входа, удаляются с локального сервера. Если *remote_name* также указан только удаленное имя входа для этого удаленного пользователя с *remoteserver* удаляется с локального сервера.  
  
 Чтобы добавить пользователей локального сервера, используйте **sp_addlogin**. Для удаления пользователей локального сервера используется **sp_droplogin**.  
  
 Удаленные имена входа требуются только в тех случаях, когда используются ранние версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 и более поздних вместо них используются имена входа связанных серверов. Используйте **sp_addlinkedsrvlogin** и **sp_droplinkedsrvlogin** для добавления и удаления имен входа связанного сервера.  
  
 **sp_dropremotelogin** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Permissions  
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
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
