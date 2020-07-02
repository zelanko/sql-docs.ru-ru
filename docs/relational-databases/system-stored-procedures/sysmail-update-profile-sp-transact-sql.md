---
title: sysmail_update_profile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_profile_sp
- sysmail_update_profile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_profile_sp
ms.assetid: eaedf7ce-a8d5-4ab9-99e0-d77d5be19e90
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3b9fd67cdd08de9ab85b0da224db970f6cd6d14d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783653"
---
# <a name="sysmail_update_profile_sp-transact-sql"></a>sysmail_update_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Изменяет описание или имя профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_update_profile_sp [ [ @profile_id = ] profile_id , ] [ [ @profile_name = ] 'profile_name' , ]  
    [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id`Идентификатор обновляемого профиля. *profile_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать хотя бы один *profile_id* или *profile_name* . Если заданы оба параметра, процедура изменяет имя профиля.  
  
`[ @profile_name = ] 'profile_name'`Имя обновляемого профиля или новое имя профиля. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать хотя бы один *profile_id* или *profile_name* . Если заданы оба параметра, процедура изменяет имя профиля.  
  
`[ @description = ] 'description'`Новое описание профиля. *Description* имеет тип **nvarchar (256)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Если одновременно указаны идентификатор и имя профиля, то процедура изменяет имя профиля на введенное и обновляет описание профиля. Если указан только один из этих аргументов, то процедура обновляет описание профиля.  
  
 Хранимая процедура **sysmail_update_profile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 **А. Изменение описания профиля**  
  
 В следующем примере изменяется описание профиля с именем `AdventureWorks Administrator` в базе данных **msdb** .  
  
```  
EXECUTE msdb.dbo.sysmail_update_profile_sp  
    @profile_name = 'AdventureWorks Administrator'  
    ,@description = 'Administrative mail profile.';  
```  
  
 **Б. Изменение имени и описания профиля**  
  
 В следующем примере изменяется имя и описание профиля с идентификатором профиля `750`.  
  
```  
EXECUTE msdb.dbo.sysmail_update_profile_sp  
    @profile_id = 750  
    ,@profile_name = 'Operator'  
    ,@description = 'Profile to send alert e-mail to operators.';  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
