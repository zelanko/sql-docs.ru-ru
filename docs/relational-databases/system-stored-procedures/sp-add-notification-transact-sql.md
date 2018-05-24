---
title: sp_add_notification (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_notification_TSQL
- sp_add_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a79b98fb3f44f3c69e7b4108502a3e6ea14e5c09
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spaddnotification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает уведомление для предупреждения.  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@alert_name=** ] **"***предупреждение***"**  
 Предупреждение для этого уведомления. *Предупреждение* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@operator_name=** ] **"***оператор***"**  
 Оператор, которому будут отправляться уведомления о предупреждении. *оператор* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@notification_method=** ] *notification_method*  
 Метод уведомления оператора. *notification_method* — **tinyint**, не имеет значения по умолчанию. *notification_method* может иметь одно или несколько из следующих значений, объединенных с **или** логический оператор.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|электронная почта|  
|**2**|Пейджер|  
|**4**|**команда net send.**|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_add_notification** должна запускаться из **msdb** базы данных.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает простой графический способ управления всей системой предупреждений. Использование среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] рекомендуется для настройки инфраструктуры предупреждений.  
  
 Чтобы в ответ на предупреждение отправить уведомление, необходимо настроить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отправки почты.  
  
 Ошибки, возникающие при отправке сообщения по электронной почте или уведомления по пейджеру, регистрируются в журнале ошибок службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_add_notification**.  
  
## <a name="examples"></a>Примеры  
 Следующий код добавляет уведомление по электронной почте для предупреждения `Test Alert`.  
  
> **Примечание:** в этом примере предполагается, что `Test Alert` уже существует и что `François Ajenstat` имеет допустимое имя оператора.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
