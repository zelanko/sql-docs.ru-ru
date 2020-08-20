---
description: sp_update_notification (Transact-SQL)
title: sp_update_notification (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_notification_TSQL
- sp_update_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatenotification
ms.assetid: 3e1c3d40-8c24-46ce-a68e-ce6c6a237fda
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 32ddc8e2afae79b458d39f577d75176ba6f9dec1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473538"
---
# <a name="sp_update_notification-transact-sql"></a>sp_update_notification (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Обновляет метод уведомления для предупреждений.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_notification  
          [@alert_name =] 'alert' ,  
     [@operator_name =] 'operator' ,  
     [@notification_method =] notification  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @alert_name = ] 'alert'` Имя предупреждения, связанного с этим уведомлением. Аргумент *Alert* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @operator_name = ] 'operator'` Оператор, который будет получать уведомления при возникновении предупреждения. Аргумент *operator* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @notification_method = ] notification` Метод, по которому оператор получает уведомления. *уведомление*имеет тип **tinyint**, не имеет значения по умолчанию и может быть одним или несколькими из этих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|электронная почта;|  
|**2**|Пейджер|  
|**4**|**команда net send.**|  
|**7**|Все методы|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_update_notification** должны запускаться из базы данных **msdb** .  
  
 Вы можете обновить уведомление для оператора, который не имеет необходимых сведений об адресе, используя указанный *notification_method*. Если при отправке сообщения по электронной почте или пейджеру происходит ошибка, она заносится в журнал ошибок агента Microsoft SQL Server.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователям должна быть предоставлена предопределенная роль сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется метод уведомления для уведомлений, отправляемых в `François Ajenstat` оповещение `Test Alert` .  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_notification  
   @alert_name = N'Test Alert',  
   @operator_name = N'François Ajenstat',  
   @notification_method = 7;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
