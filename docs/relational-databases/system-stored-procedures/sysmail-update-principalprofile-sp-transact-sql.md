---
title: sysmail_update_principalprofile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a2af55b8c5354dd90e80a0a2a9d149f56abdef27
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533870"
---
# <a name="sysmailupdateprincipalprofilesp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет данные о взаимосвязи между каким-либо участником и профилем.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @principal_id = ] principal_id` Идентификатор пользователя базы данных или роли в **msdb** базы данных для изменения взаимосвязи. *principal_id* — **int**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* должен быть указан.  
  
`[ @principal_name = ] 'principal_name'` Имя пользователя базы данных или роли в **msdb** базы данных для обновления взаимосвязи. *principal_name* — **sysname**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* может быть указан.  
  
`[ @profile_id = ] profile_id` Идентификатор профиля для изменения взаимосвязи. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @profile_name = ] 'profile_name'` Имя профиля для изменения взаимосвязи. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @is_default = ] 'is_default'` Является ли этот профиль профилем по умолчанию для пользователя базы данных. Пользователь базы данных может иметь только один профиль по умолчанию. *is_default* — **бит**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Данная хранимая процедура изменяется в зависимости от того, является ли заданный профиль профилем по умолчанию для пользователя базы данных. Пользователь базы данных может иметь только один личный профиль по умолчанию.  
  
 Если имя участника взаимосвязи является **открытый** или идентификатор участника взаимосвязи является **0**, этот хранимая процедура изменяет открытый профиль. Может быть только один открытый (public) профиль по умолчанию.  
  
 Когда **@is_default** — "**1**" и участник связан с более чем одним профилем, то заданный профиль становится профилем по умолчанию для участника. Профиль, который ранее был профилем по умолчанию, все еще связан с участником, но не является более профилем по умолчанию.  
  
 Хранимая процедура **sysmail_update_principalprofile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Установка профиля в открытый профиль по умолчанию для базы данных**  
  
 Следующий пример устанавливает профиль `General Use Profile` в открытый профиль по умолчанию для пользователей в **msdb** базы данных.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **Б. Установка профиля по частный профиль по умолчанию для пользователя**  
  
 Следующий пример устанавливает профиль `AdventureWorks Administrator` быть для участника профилем по умолчанию `ApplicationUser` в **msdb** базы данных. Профиль должен быть заранее связан с участником. Профиль, который ранее был профилем по умолчанию, все еще связан с участником, но не является более профилем по умолчанию.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
