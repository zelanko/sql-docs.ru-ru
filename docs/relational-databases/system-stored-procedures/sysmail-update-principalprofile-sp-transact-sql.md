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
ms.openlocfilehash: dd9644253302c6a577c6cc3923bb3a9e3a0d8c0e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037379"
---
# <a name="sysmail_update_principalprofile_sp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
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
`[ @principal_id = ] principal_id`Идентификатор пользователя или роли базы данных в базе данных **msdb** для изменения взаимосвязи. *principal_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *principal_id* , либо *principal_name* .  
  
`[ @principal_name = ] 'principal_name'`Имя пользователя или роли базы данных в базе данных **msdb** для обновления взаимосвязи. Аргумент *principal_name* имеет тип **sysname**и значение по умолчанию NULL. Можно указать либо *principal_id* , либо *principal_name* .  
  
`[ @profile_id = ] profile_id`Идентификатор профиля для изменения взаимосвязи. *profile_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @profile_name = ] 'profile_name'`Имя профиля для изменения взаимосвязи. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @is_default = ] 'is_default'`Указывает, является ли этот профиль профилем по умолчанию для пользователя базы данных. Пользователь базы данных может иметь только один профиль по умолчанию. *is_default* имеет **бит**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Данная хранимая процедура изменяется в зависимости от того, является ли заданный профиль профилем по умолчанию для пользователя базы данных. Пользователь базы данных может иметь только один личный профиль по умолчанию.  
  
 Если имя участника для ассоциации является **открытым** или идентификатор субъекта для ассоциации равен **0**, эта хранимая процедура изменяет открытый профиль. Может быть только один открытый (public) профиль по умолчанию.  
  
 Если ** \@is_default** имеет значение**1**и участник связан с более чем одним профилем, указанный профиль становится профилем по умолчанию для участника. Профиль, который ранее был профилем по умолчанию, все еще связан с участником, но не является более профилем по умолчанию.  
  
 Хранимая процедура **sysmail_update_principalprofile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **А. Установка профиля в открытый профиль по умолчанию для базы данных**  
  
 В следующем примере профиль `General Use Profile` задается как открытый профиль по умолчанию для пользователей в базе данных **msdb** .  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **Б. Настройка профиля в профиль по умолчанию для пользователя**  
  
 В следующем примере профиль `AdventureWorks Administrator` задается как профиль по умолчанию для участника `ApplicationUser` в базе данных **msdb** . Профиль должен быть заранее связан с участником. Профиль, который ранее был профилем по умолчанию, все еще связан с участником, но не является более профилем по умолчанию.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
