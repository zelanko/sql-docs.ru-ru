---
title: sp_help_notification (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_notification
- sp_help_notification_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_notification
ms.assetid: 0273457f-9d2a-4a6f-9a16-6a6bf281cba0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dbba9ea2f9df7e9a9fd154193c8f52fe904899c7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820462"
---
# <a name="sp_help_notification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит список предупреждений для заданного оператора или список операторов для заданного предупреждения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_notification  
     [ @object_type = ] 'object_type' ,  
     [ @name = ] 'name' ,  
     [ @enum_type = ] 'enum_type' ,   
     [ @notification_method = ] notification_method   
     [ , [ @target_name = ] 'target_name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @object_type = ] 'object_type'`Тип возвращаемых данных. *object_type*имеет **тип char (9)** и не имеет значения по умолчанию. *object_type* могут быть предупреждениями, в которых перечислены предупреждения, назначенные указанному имени оператора *,* или операторы, в которых перечислены операторы, отвечающие за предоставленное имя предупреждения *.*  
  
`[ @name = ] 'name'`Имя оператора (если *object_type* — операторы) или имя предупреждения (если *OBJECT_TYPE* — это Alerts). Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @enum_type = ] 'enum_type'`Возвращаемые сведения о *object_type*. в большинстве случаев *ENUM_TYPE* фактически. *enum_type*имеет **тип char (10)**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|ACTUAL|Выводит только *object_types* , связанные с *именем*.|  
|ALL|Список всех*object_types* , включая те, которые не связаны с *именем*.|  
|TARGET|Перечисляет только *object_types* , соответствующие заданному *target_name*, независимо от связи с*именем*.|  
  
`[ @notification_method = ] notification_method`Числовое значение, определяющее возвращаемые столбцы метода уведомления. *notification_method* имеет тип **tinyint**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**1**|Электронная почта. возвращает только столбец **use_email** .|  
|**2**|Пейджер: возвращает только столбец **use_pager** .|  
|**4**|NetSend: возвращает только столбец **use_netsend** .|  
|**7**|Все: возвращает все столбцы.|  
  
`[ @target_name = ] 'target_name'`Имя предупреждения для поиска (если *object_type* — оповещения) или имя оператора для поиска (если *object_type* является операторами). *target_name* требуется только в том случае, если *enum_type* является целевым объектом. Аргумент *target_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-valves"></a>Значения кодов возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если *object_type* — **предупреждения**, результирующий набор перечисляет все предупреждения для данного оператора.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Идентификатор предупреждения.|  
|**alert_name**|**sysname**|Имя предупреждения.|  
|**use_email**|**int**|Уведомление оператора происходит по электронной почте.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**use_pager**|**int**|Уведомление оператора происходит по пейджеру.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**use_netsend**|**int**|Уведомление оператора происходит с помощью сетевого всплывающего окна.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**has_email**|**int**|Количество уведомлений, отправленных для данного предупреждения по электронной почте.|  
|**has_pager**|**int**|Количество уведомлений, отправленных для данного предупреждения по пейджеру.|  
|**has_netsend**|**int**|Число уведомлений **net send** , отправленных для этого предупреждения.|  
  
 Если **object_type** — **Операторы**, результирующий набор перечисляет все операторы для данного предупреждения.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**operator_id**|**int**|Идентификационный номер оператора.|  
|**operator_name**|**sysname**|Имя оператора.|  
|**use_email**|**int**|Уведомление оператора происходит по электронной почте.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**use_pager**|**int**|Уведомление оператора происходит по пейджеру.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**use_netsend**|**int**|Для уведомления оператора используется всплывающее сетевое сообщение.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**has_email**|**int**|У оператора есть адрес электронной почты.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**has_pager**|**int**|У оператора есть адрес пейджера.<br /><br /> **1** = да<br /><br /> **0** = нет|  
|**has_netsend**|**int**|Оператор имеет настроенное уведомление net send.<br /><br /> **1** = да<br /><br /> **0** = нет|  
  
## <a name="remarks"></a>Remarks  
 Эта хранимая процедура должна запускаться из базы данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-alerts-for-a-specific-operator"></a>A. Список предупреждений для указанного оператора  
 В следующем примере возвращаются все предупреждения, для которых оператор `François Ajenstat` получает уведомления любого вида.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_notification   
    @object_type = N'ALERTS',  
    @name = N'François Ajenstat',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
### <a name="b-listing-operators-for-a-specific-alert"></a>Б. Список операторов для указанного предупреждения  
 В следующем примере возвращаются все операторы, которые получают уведомления любого вида для предупреждения `Test Alert`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_notification  
    @object_type = N'OPERATORS',  
    @name = N'Test Alert',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
