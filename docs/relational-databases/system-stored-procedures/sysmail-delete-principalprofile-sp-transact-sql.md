---
description: sysmail_delete_principalprofile_sp (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1cf4424f440ff8d03aa63933dbc4e661556e2106
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419308"
---
# <a name="sysmail_delete_principalprofile_sp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет разрешение пользователя или роли базы данных на использование открытого или частного профиля компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @principal_id = ] principal_id` Идентификатор пользователя или роли базы данных в базе данных **msdb** для удаления связи. *principal_id* имеет **тип int**и значение по умолчанию NULL. Чтобы сделать открытый профиль частным, укажите идентификатор участника **0** или имя участника **"Public"**. Необходимо указать либо *principal_id* , либо *principal_name* .  
  
`[ @principal_name = ] 'principal_name'` Имя пользователя или роли базы данных в базе данных **msdb** для удаления связи. Аргумент *principal_name* имеет тип **sysname**и значение по умолчанию NULL. Чтобы сделать открытый профиль частным, укажите идентификатор участника **0** или имя участника **"Public"**. Необходимо указать либо *principal_id* , либо *principal_name* .  
  
`[ @profile_id = ] profile_id` Идентификатор профиля для удаляемой связи. *profile_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @profile_name = ] 'profile_name'` Имя профиля для удаления связи. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Чтобы создать общий профиль в частном профиле, укажите для имени участника значение **"Public"** или **0** для идентификатора участника.  
  
 Будьте осторожны, удаляя разрешения для частного профиля пользователя по умолчанию или открытого профиля по умолчанию. Если профиль по умолчанию недоступен, **sp_send_dbmail** требует имя профиля в качестве аргумента. Поэтому удаление профиля по умолчанию может привести к сбою вызовов **sp_send_dbmail** . Дополнительные сведения см. в разделе [sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Хранимая процедура **sysmail_delete_principalprofile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано удаление связи между **администратором Profile AdventureWorks** и именем входа **аппликатионусер** в базе данных **msdb** .  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
