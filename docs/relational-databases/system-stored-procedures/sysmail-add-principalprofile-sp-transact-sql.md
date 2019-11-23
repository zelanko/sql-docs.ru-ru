---
title: sysmail_add_principalprofile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_principalprofile_sp_TSQL
- sysmail_add_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_principalprofile_sp
ms.assetid: b2a0b313-abb9-4c23-8511-db77ca8172b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: fedc7e0dd7fe71feb0b0da1f00f2a7f996c6129c
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305059"
---
# <a name="sysmail_add_principalprofile_sp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешение на использование профиля Database Mail участнику базы данных msdb. Участник базы данных должен сопоставляться с пользователем проверки подлинности SQL Server, пользователем Windows или группой Windows.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @principal_id = ] principal_id` идентификатор пользователя или роли базы данных в базе данных **msdb** для сопоставления. *principal_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *principal_id* , либо *principal_name* . *Principal_id* **0** делает этот профиль открытым профилем, предоставляя доступ ко всем субъектам в базе данных.  
  
`[ @principal_name = ] 'principal_name'` имя пользователя или роли базы данных в базе данных **msdb** для сопоставления. Аргумент *principal_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *principal_id* , либо *principal_name* . *Principal_name* **"Public"** делает этот профиль открытым профилем, предоставляя доступ ко всем субъектам в базе данных.  
  
`[ @profile_id = ] profile_id` идентификатор профиля для ассоциации. *profile_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @profile_name = ] 'profile_name'` имя профиля для ассоциации. Аргумент *profile_name* имеет тип **sysname**и не имеет значения по умолчанию. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @is_default = ] is_default` указывает, является ли этот профиль профилем по умолчанию для участника. Участник должен иметь ровно один профиль по умолчанию. *is_default* имеет **бит**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Чтобы сделать профиль общедоступным, укажите **\@principal_id** **0** или **\@principal_name** **Public**. Открытый профиль доступен для всех пользователей в базе данных **msdb** , хотя пользователи также должны быть членами **роли DatabaseMailUserRole** для выполнения **sp_send_dbmail**.  
  
 Пользователь базы данных может иметь только один профиль по умолчанию. Если **\@is_default** имеет значение**1**, а пользователь уже связан с одним или несколькими профилями, указанный профиль становится профилем по умолчанию для пользователя. Профиль, который ранее был профилем по умолчанию, остается ассоциированным с пользователем, но уже не является профилем по умолчанию.  
  
 Если **\@is_default** имеет значение "**0**", а другая ассоциация не существует, хранимая процедура возвращает ошибку.  
  
 Хранимая процедура **sysmail_add_principalprofile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **А. Создание связи с установкой профиля по умолчанию**  
  
 В следующем примере создается ассоциация между профилем с именем `AdventureWorks Administrator Profile` и `ApplicationUser`ом пользователя базы данных **msdb** . Указанный профиль становится для пользователя профилем по умолчанию.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **Б. Создание профиля с открытым профилем по умолчанию**  
  
 В следующем примере профиль `AdventureWorks Public Profile` открытый профиль по умолчанию для пользователей в базе данных **msdb** .  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>См. также статью  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых &#40;процедур TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
