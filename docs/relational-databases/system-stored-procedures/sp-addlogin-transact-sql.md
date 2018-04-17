---
title: sp_addlogin (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addlogin
- sp_addlogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlogin
ms.assetid: 030f19c3-a5e3-4b53-bfc4-de4bfca0fddc
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f191cf305941d837a65708aea62527c0649b6e7f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spaddlogin-transact-sql"></a>sp_addlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новое имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], позволяющее пользователю подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с применением проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) вместо него.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addlogin [ @loginame = ] 'login'   
    [ , [ @passwd = ] 'password' ]   
    [ , [ @defdb = ] 'database' ]   
    [ , [ @deflanguage = ] 'language' ]   
    [ , [ @sid = ] sid ]   
    [ , [ @encryptopt = ] 'encryption_option' ]   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @loginame=] '*входа*"  
 Имя входа. *Имя входа* — **sysname**, не имеет значения по умолчанию.  
  
 [ @passwd=] '*пароль*"  
 Пароль имени входа. *пароль* — **sysname**, значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 [ @defdb=] '*базы данных*"  
 База данных, используемая по умолчанию именем входа (база данных, к которой подключается пользователь с этим именем после входа в систему). *База данных* — **sysname**, значение по умолчанию **master**.  
  
 [ @deflanguage=] '*языка*"  
 Язык по умолчанию для имени входа. *Язык* — **sysname**, значение по умолчанию NULL. Если *язык* не указан, значение по умолчанию *языка* нового имени входа установлена на текущий язык по умолчанию сервера.  
  
 [ @sid=] '*sid*"  
 Идентификатор безопасности (SID). *SID* — **varbinary(16)**, значение по умолчанию NULL. Если *sid* имеет значение NULL, система сама формирует SID для нового имени входа. Несмотря на использование **varbinary** тип данных значения, отличные от NULL должно быть ровно 16 байт и не должен существовать. Указание *sid* может быть полезным, например, когда скриптах или переносе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имена входа с одного сервера на другой, нужно, чтобы иметь тот же SID на разных серверах.  
  
 [ @encryptopt=] '*encryption_option*"  
 Этот аргумент определяет, передается ли пароль в виде открытого текста или в виде его хэша. Шифрование при этом не выполняется. Слово «шифрование» используется в этом контексте для обратной совместимости. Если в процедуру передан открытый пароль, он хэшируется. Хэш сохраняется. *encryption_option* — **varchar(20)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|NULL|Пароль передан как открытый текст. Это значение по умолчанию.|  
|**skip_encryption**|Хэширование пароля уже выполнено. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен сохранить его значение без повторного хэширования.|  
|**skip_encryption_old**|Указанный пароль был хэширован более ранней версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен сохранить его значение без повторного хэширования. Этот вариант предоставлен только для выполнения обновлений.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать от 1 до 128 символов, включая буквы, символы и цифры. Имена входа не может содержать обратную косую черту (\\); быть зарезервированными именами, такими как sa или public, или уже существует; или иметь значение NULL или пустая строка (`''`).  
  
 Если предоставлено имя базы данных по умолчанию, к ней можно подключиться, не выполняя инструкцию USE. Тем не менее, нельзя использовать базу данных по умолчанию, пока вы получают доступ к этой базе данных владельцем базы данных (с помощью [sp_adduser](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md) или [sp_addrolemember](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)) или [sp_addrole](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md).  
  
 Номер SID — это идентификатор GUID, однозначно определяющий имя входа на сервере.  
  
 Изменение языка по умолчанию на сервере не приводит к изменению языка по умолчанию существующих имен входа. Чтобы изменить язык по умолчанию сервера, используйте [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 С помощью **skip_encryption** отключение пароля хэширования полезно, если пароль уже хэширован при добавлении имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если пароль был хэширован более ранней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте **skip_encryption_old**.  
  
 Хранимая процедура sp_addlogin не может быть выполнена в пользовательской транзакции.  
  
 В следующей таблице указаны некоторые хранимые процедуры, используемые совместно с sp_addlogin.  
  
|Хранимая процедура|Описание|  
|----------------------|-----------------|  
|[sp_grantlogin](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)|Добавляет пользователя или группу Windows.|  
|[sp_password](../../relational-databases/system-stored-procedures/sp-password-transact-sql.md)|Изменяет пароль пользователя.|  
|[sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)|Изменяет назначенную пользователю базу данных по умолчанию.|  
|[sp_defaultlanguage](../../relational-databases/system-stored-procedures/sp-defaultlanguage-transact-sql.md)|Изменяет назначенный пользователю язык по умолчанию.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-sql-server-login"></a>A. Создание имени входа на SQL Server  
 В следующем примере создается имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя `Victoria` с паролем `B1r12-36` без указания базы данных по умолчанию.  
  
```  
EXEC sp_addlogin 'Victoria', 'B1r12-36';  
GO  
```  
  
### <a name="b-creating-a-sql-server-login-that-has-a-default-database"></a>Б. Создание имени входа на SQL Server с базой данных по умолчанию  
 В следующем примере создается имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя `Albert` с паролем `B5432-3M6` и базой данных `corporate` по умолчанию.  
  
```  
EXEC sp_addlogin 'Albert', 'B5432-3M6', 'corporate';  
GO  
```  
  
### <a name="c-creating-a-sql-server-login-that-has-a-different-default-language"></a>В. Создание имени входа на SQL Server с другим языком по умолчанию  
 В следующем примере создается имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя `TzTodorov` с паролем `709hLKH7chjfwv`, базой данных `AdventureWorks2012` и языком `Bulgarian` по умолчанию.  
  
```  
EXEC sp_addlogin 'TzTodorov', '709hLKH7chjfwv', 'AdventureWorks2012', N'български'  
```  
  
### <a name="d-creating-a-sql-server-login-that-has-a-specific-sid"></a>Г. Создание имени входа на SQL Server с конкретным SID  
 В следующем примере создается имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя `Michael` с паролем `B548bmM%f6`, базой данных по умолчанию `AdventureWorks2012`, языком по умолчанию `us_english` и SID, равным `0x0123456789ABCDEF0123456789ABCDEF`.  
  
```  
EXEC sp_addlogin 'Michael', 'B548bmM%f6', 'AdventureWorks2012', 'us_english', 0x0123456789ABCDEF0123456789ABCDEF  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_droplogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Хранимая процедура sp_revokelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
