---
title: sp_add_notification (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_notification_TSQL
- sp_add_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60bb289f0fd6d7b7dd1034630929998d32cc59d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68115060"
---
# <a name="sp_add_notification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает уведомление для предупреждения.  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @alert_name = ] 'alert'`Оповещение для этого уведомления. Аргумент *Alert* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @operator_name = ] 'operator'`Оператор, уведомляющий о возникновении предупреждения. Аргумент *operator* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @notification_method = ] notification_method`Метод, по которому оператор получает уведомления. *notification_method* имеет тип **tinyint**и не имеет значения по умолчанию. *notification_method* может быть одним или несколькими из этих значений в сочетании с логическим оператором **or** .  
  
|Значение|Description|  
|-----------|-----------------|  
|**1**|электронная почта;|  
|**2**|Пейджер|  
|**4**|**NET SEND**|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_notification** должны запускаться из базы данных **msdb** .  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]предоставляет простой графический способ управления всей системой предупреждений. Использование среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] рекомендуется для настройки инфраструктуры предупреждений.  
  
 Чтобы в ответ на предупреждение отправить уведомление, необходимо настроить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отправки почты.  
  
 Ошибки, возникающие при отправке сообщения по электронной почте или уведомления по пейджеру, регистрируются в журнале ошибок службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_add_notification**.  
  
## <a name="examples"></a>Примеры  
 Следующий код добавляет уведомление по электронной почте для предупреждения `Test Alert`.  
  
> **Примечание.** В этом примере предполагается, что `Test Alert` уже `François Ajenstat` существует и является допустимым именем оператора.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также раздел  
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
