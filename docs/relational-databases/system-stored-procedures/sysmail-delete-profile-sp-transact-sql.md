---
title: sysmail_delete_profile_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_profile_sp
- sysmail_delete_profile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_profile_sp
ms.assetid: 71998653-4a02-446d-b6f7-50646a29e8a2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e6e39ee5afb5171eee87b30ab83b9636f91a4b0b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832477"
---
# <a name="sysmail_delete_profile_sp-transact-sql"></a>sysmail_delete_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет профиль электронной почты, используемый компонентом Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_profile_sp  { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id`Идентификатор профиля удаляемого профиля. *profile_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
`[ @profile_name = ] 'profile_name'`Имя удаляемого профиля. Аргумент *profile_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать либо *profile_id* , либо *profile_name* .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Удаление профиля не приведет к удалению всех учетных записей, используемых данным профилем.  
  
 Эта хранимая процедура удаляет профиль в независимости от того, имеют ли пользователи к нему доступ. Будьте внимательны при удалении личного профиля по умолчанию для пользователя или открытого профиля по умолчанию для базы данных **msdb** . Если профиль по умолчанию недоступен, **sp_send_dbmail** требует имя профиля в качестве аргумента. Поэтому удаление профиля по умолчанию может привести к сбою вызовов **sp_send_dbmail** . Дополнительные сведения см. в разделе [sp_send_dbmail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Хранимая процедура **sysmail_delete_profile_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется профиль с именем `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
