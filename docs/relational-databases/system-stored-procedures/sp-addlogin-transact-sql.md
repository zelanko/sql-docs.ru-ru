---
title: sp_addlogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addlogin
- sp_addlogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlogin
ms.assetid: 030f19c3-a5e3-4b53-bfc4-de4bfca0fddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 06629b059afffe3baa0a34caec1337d7bc3f2517
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757991"
---
# <a name="sp_addlogin-transact-sql"></a>sp_addlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Создает новое имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], позволяющее пользователю подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с применением проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) .  
  
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
 [ @loginame =] "*Login*"  
 Имя входа. Аргумент *Login* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @passwd =] "*пароль*"  
 Пароль имени входа. Аргумент *Password* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 [ @defdb =] "*база данных*"  
 База данных, используемая по умолчанию именем входа (база данных, к которой подключается пользователь с этим именем после входа в систему). Аргумент *Database* имеет тип **sysname**и значение по умолчанию **master**.  
  
 [ @deflanguage =] "*язык*"  
 Язык по умолчанию для имени входа. *Language* имеет тип **sysname**и значение по умолчанию NULL. Если *язык* не указан, в качестве *языка* по умолчанию для нового имени входа устанавливается текущий язык по умолчанию сервера.  
  
 [ @sid =] "*SID*"  
 Идентификатор безопасности (SID). *идентификатор безопасности* имеет тип **varbinary (16)** и значение по умолчанию NULL. Если *SID* имеет значение null, система создает идентификатор безопасности для нового имени входа. Несмотря на использование типа данных **varbinary** , значения, отличные от NULL, должны иметь длину ровно 16 байт и не должны существовать. Указание *идентификатора безопасности* полезно, например, при создании скриптов или при перемещении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имен входа с одного сервера на другой, если имена входа должны иметь одинаковый идентификатор безопасности на разных серверах.  
  
 [ @encryptopt =] "*encryption_option*"  
 Этот аргумент определяет, передается ли пароль в виде открытого текста или в виде его хэша. Шифрование при этом не выполняется. Слово «шифрование» используется в этом контексте для обратной совместимости. Если в процедуру передан открытый пароль, он хэшируется. Хэш сохраняется. *encryption_option* имеет тип **varchar (20)** и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|NULL|Пароль передан как открытый текст. Это значение по умолчанию.|  
|**skip_encryption**|Хэширование пароля уже выполнено. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен сохранить его значение без повторного хэширования.|  
|**skip_encryption_old**|Указанный пароль был хэширован более ранней версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен сохранить его значение без повторного хэширования. Этот вариант предоставлен только для выполнения обновлений.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать от 1 до 128 символов, включая буквы, символы и цифры. Имена входа не могут содержать обратную косую черту ( \\ ); быть зарезервированным именем для входа, например SA или public или уже существует; либо иметь значение null или быть пустой строкой ( `''` ).  
  
 Если предоставлено имя базы данных по умолчанию, к ней можно подключиться, не выполняя инструкцию USE. Однако нельзя использовать базу данных по умолчанию, пока владелец базы данных не получит доступ к этой базе данных (с помощью [sp_adduser](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md) или [sp_addrolemember](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)) или [sp_addrole](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md).  
  
 Номер SID — это идентификатор GUID, однозначно определяющий имя входа на сервере.  
  
 Изменение языка по умолчанию на сервере не приводит к изменению языка по умолчанию существующих имен входа. Чтобы изменить язык по умолчанию сервера, используйте [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 Использование **skip_encryption** для подавления хэширования паролей полезно, если пароль уже хэширован при добавлении имени входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если пароль был хэширован более ранней версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используйте **skip_encryption_old**.  
  
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
 [Создание имени входа &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
