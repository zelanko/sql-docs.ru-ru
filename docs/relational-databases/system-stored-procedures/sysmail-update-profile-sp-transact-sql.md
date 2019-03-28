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
manager: craigg
ms.openlocfilehash: d2b1616fdf7b690d61c6a2605cc15da2508a3fb9
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534666"
---
# <a name="sysmailupdateprofilesp-transact-sql"></a>sysmail_update_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет описание или имя профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_update_profile_sp [ [ @profile_id = ] profile_id , ] [ [ @profile_name = ] 'profile_name' , ]  
    [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id` Идентификатор профиля для обновления. *profile_id* — **int**, значение по умолчанию NULL. Хотя бы один из *profile_id* или *profile_name* должен быть указан. Если заданы оба параметра, процедура изменяет имя профиля.  
  
`[ @profile_name = ] 'profile_name'` Имя профиля или новое имя для профиля. *profile_name* — **sysname**, значение по умолчанию NULL. Хотя бы один из *profile_id* или *profile_name* должен быть указан. Если заданы оба параметра, процедура изменяет имя профиля.  
  
`[ @description = ] 'description'` Новое описание для профиля. *Описание* — **nvarchar(256)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если одновременно указаны идентификатор и имя профиля, то процедура изменяет имя профиля на введенное и обновляет описание профиля. Если указан только один из этих аргументов, то процедура обновляет описание профиля.  
  
 Хранимая процедура **sysmail_update_profile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Изменение описания профиля**  
  
 В следующем примере изменяется описание профиля с именем `AdventureWorks Administrator` в **msdb** базы данных.  
  
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
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Создайте учетную запись почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
