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
manager: craigg
ms.openlocfilehash: cf12b97028d3d98f7d5cc5ab034db95411d913dc
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528506"
---
# <a name="sysmailaddprincipalprofilesp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет пользователю или роли базы данных разрешение на использование профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @principal_id = ] principal_id` Идентификатор пользователя базы данных или роли в **msdb** базы данных для ассоциации. *principal_id* — **int**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* должен быть указан. Объект *principal_id* из **0** профиль становится общедоступной, предоставив этому пользователю доступ всем участникам в базе данных.  
  
`[ @principal_name = ] 'principal_name'` Имя пользователя базы данных или роли в **msdb** базы данных для ассоциации. *principal_name* — **sysname**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* должен быть указан. Объект *principal_name* из **'public'** профиль становится общедоступной, предоставив этому пользователю доступ всем участникам в базе данных.  
  
`[ @profile_id = ] profile_id` Идентификатор профиля для взаимосвязи. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @profile_name = ] 'profile_name'` Имя профиля для взаимосвязи. *profile_name* — **sysname**, не имеет значения по умолчанию. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @is_default = ] is_default` Указывает, является ли этот профиль для участника профилем по умолчанию. Участник должен иметь ровно один профиль по умолчанию. *is_default* — **бит**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Чтобы сделать профиль открытым, укажите **@principal_id** из **0** или **@principal_name** из **открытый**. Открытый профиль доступен всем пользователям в **msdb** базы данных, хотя пользователи также должны быть членом **DatabaseMailUserRole** для выполнения **sp_send_dbmail**.  
  
 Пользователь базы данных может иметь только один профиль по умолчанию. Когда **@is_default** — "**1**" и пользователь уже связан с одним или несколькими профилями, то заданный профиль становится профилем по умолчанию для пользователя. Профиль, который ранее был профилем по умолчанию, остается ассоциированным с пользователем, но уже не является профилем по умолчанию.  
  
 Когда **@is_default** — "**0**" и никаких других ассоциаций нет, хранимая процедура возвращает ошибку.  
  
 Хранимая процедура **sysmail_add_principalprofile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Создание ассоциации с профилем, определение профиля по умолчанию**  
  
 В следующем примере создается связь между профиля с именем `AdventureWorks Administrator Profile` и **msdb** пользователя базы данных `ApplicationUser`. Указанный профиль становится для пользователя профилем по умолчанию.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **Б. Определение открытого профиля по умолчанию**  
  
 В следующем примере создается профиль `AdventureWorks Public Profile` открытый профиль по умолчанию для пользователей в **msdb** базы данных.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
