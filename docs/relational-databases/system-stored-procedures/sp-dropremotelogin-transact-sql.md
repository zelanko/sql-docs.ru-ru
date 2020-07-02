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
author: VanMSFT
ms.openlocfilehash: 257592ce6bd3c8080a6f4244a7528e79259e5cfa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783791"
---
# <a name="sp_dropremotelogin-transact-sql"></a>sp_dropremotelogin (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @remoteserver = ] 'remoteserver'`Имя удаленного сервера, сопоставленного с удаляемым удаленным именем входа. Аргумент *remoteserver* имеет тип **sysname**и не имеет значения по умолчанию. *Удаленный* том уже должен существовать.  
  
`[ @loginame = ] 'login'`Необязательное имя входа на локальном сервере, связанное с удаленным сервером. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. *имя входа* должно уже существовать, если оно указано.  
  
`[ @remotename = ] 'remote_name'`Необязательное имя удаленного входа, сопоставленное с *именем входа* при входе с удаленного сервера. Аргумент *remote_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если указан только параметр *remoteserver* , то все удаленные имена входа для этого удаленного сервера удаляются с локального сервера. Если указано также *имя для входа* , то все удаленные имена *входа с удаленного* сервера, сопоставленные с этим конкретным локальным именем входа, удаляются из локальной службы. Если также указан параметр *remote_name* , то только удаленное имя входа удаленного пользователя из *remoteserver* удаляется с локального сервера.  
  
 Чтобы добавить пользователей локального сервера, используйте **sp_addlogin**. Чтобы удалить пользователей локального сервера, используйте **sp_droplogin**.  
  
 Удаленные имена входа требуются только в тех случаях, когда используются ранние версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 и более поздних вместо них используются имена входа связанных серверов. Для добавления и удаления имен входа на связанный сервер используйте **sp_addlinkedsrvlogin** и **sp_droplinkedsrvlogin** .  
  
 **sp_dropremotelogin** не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенных ролях сервера **sysadmin** или **администратора** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-all-remote-logins-for-a-remote-server"></a>A. Удаление всех удаленных имен входа с удаленного сервера  
 Следующий пример удаляет вхождение для удаленного сервера `ACCOUNTS` и поэтому удаляет все сопоставления между именами входа на локальном сервере и удаленными именами входа на удаленном сервере.  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-dropping-a-login-mapping"></a>Б. Удаление сопоставления имени входа  
 Следующий пример удаляет сопоставление удаленных имен входа с удаленного сервера `ACCOUNTS` на локальное имя входа `Albert`.  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-dropping-a-remote-user"></a>В. Удаление удаленного пользователя  
 Следующий пример удаляет имя входа `Chris` на удаленном сервере `ACCOUNTS`, которое сопоставлено локальному имени входа `salesmgr`.  
  
```sql
EXEC sp_dropremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
