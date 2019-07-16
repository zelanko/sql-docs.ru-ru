---
title: sysmail_delete_principalprofile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86f9566ce86423939aff22fc37331c5c9db89904
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909211"
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет разрешение пользователя или роли базы данных на использование открытого или частного профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @principal_id = ] principal_id` Идентификатор пользователя базы данных или роли в **msdb** базы данных для удаляемой взаимосвязи. *principal_id* — **int**, значение по умолчанию NULL. Чтобы сделать открытый профиль частным, укажите идентификатор участника **0** или имя участника- **'public'** . Либо *principal_id* или *principal_name* должен быть указан.  
  
`[ @principal_name = ] 'principal_name'` Имя пользователя базы данных или роли в **msdb** базы данных для удаляемой взаимосвязи. *principal_name* — **sysname**, значение по умолчанию NULL. Чтобы сделать открытый профиль частным, укажите идентификатор участника **0** или имя участника- **'public'** . Либо *principal_id* или *principal_name* должен быть указан.  
  
`[ @profile_id = ] profile_id` — Идентификатор профиля для удаляемой взаимосвязи. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
`[ @profile_name = ] 'profile_name'` — Имя профиля для удаляемой взаимосвязи. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Чтобы сделать открытый профиль частным, укажите **'public'** имя участника или **0** идентификатор участника.  
  
 Будьте осторожны, удаляя разрешения для частного профиля пользователя по умолчанию или открытого профиля по умолчанию. При наличии нет профиля по умолчанию **sp_send_dbmail** необходимо указать имя профиля в качестве аргумента. Таким образом, удаление профиля по умолчанию может привести к вызовы **sp_send_dbmail** переход на другой. Дополнительные сведения см. в разделе [sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Хранимая процедура **sysmail_delete_principalprofile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано удаление ассоциации между профилем **AdventureWorks Administrator** и имя входа **ApplicationUser** в **msdb** базы данных.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
