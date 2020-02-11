---
title: sp_addremotelogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb45ce1c3e1786eb5a9a3cd630741dd4df773c40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030959"
---
# <a name="sp_addremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет новый идентификатор удаленного имени входа на локальный сервер. Это позволяет удаленным серверам подключаться и выполнять удаленные вызовы процедуры (RPC).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]Вместо этого используйте связанные серверы и хранимые процедуры связанного сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @remoteserver **=** ] **\**"_remoteserver_**\"**  
 Имя удаленного сервера, к которому применяется удаленный вход. Аргумент *remoteserver* имеет тип **sysname**и не имеет значения по умолчанию. Если указан только параметр *remoteserver* , все пользователи на *remoteserver* сопоставляются с существующими именами входа на локальном сервере. Сервер должен быть известен локальному серверу. Его можно добавить при помощи хранимой процедуры sp_addserver. Когда пользователи на *remoteserver* подключаются к локальному серверу, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на котором выполняется удаленная хранимая процедура, они подключаются как локальное имя входа, совпадающее с собственным именем входа на *remoteserver*. *remoteserver* — это сервер, инициирующий удаленный вызов процедуры.  
  
 [ @loginame **=** ] **"**_Login_**"**  
 Идентификатор имени входа для пользователя локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *Login* имеет тип **sysname**и значение по умолчанию NULL. *имя входа*должно уже существовать на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если указано *имя входа* , все пользователи на *remoteserver* сопоставляются с определенным локальным именем входа. Когда пользователи на *remoteserver* подключаются к локальному [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляру для выполнения удаленной хранимой процедуры, они подключаются к *имени входа*.  
  
 [ @remotename **=** ] **"**_remote_name_**"**  
 Идентификатор имени входа пользователя на удаленном сервере. Аргумент *remote_name* имеет тип **sysname**и значение по умолчанию NULL. *remote_name* должен существовать на *remoteserver*. Если указан *remote_name* , то конкретный пользователь *remote_name* сопоставляется с *именем входа* на локальном сервере. Когда *remote_name* на *remoteserver* соединяется с локальным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения удаленной хранимой процедуры, она подключается как *имя входа*. Идентификатор входа *remote_name* может отличаться от идентификатора имени входа на удаленном сервере, *имени входа*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 Два выполнения распределенных запросов используйте хранимую процедуру sp_addlinkedsrvlogin.  
  
 Хранимую процедуру sp_addremotelogin нельзя использовать внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Хранимую процедуру sp_addremotelogin могут выполнять только члены предопределенных ролей сервера sysadmin и securityadmin.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-mapping-one-to-one"></a>A. Сопоставление «один к одному»  
 Следующий пример сопоставляет удаленные имена локальным, если имена входа пользователей на удаленном сервере `ACCOUNTS` и на локальном сервере совпадают.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>Б. Сопоставление «многие к одному»  
 В следующем примере создается запись, которая сопоставляет всех пользователей удаленного сервера `ACCOUNTS` локальному идентификатору входа `Albert`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>В. Использование явного сопоставления «один к одному»  
 Следующий пример сопоставляет удаленное имя входа удаленного пользователя `Chris` на удаленном сервере `ACCOUNTS` локальному пользователю `salesmgr`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
