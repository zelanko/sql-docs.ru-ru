---
title: dbo.sysoperators (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3796714cbdfb55900447bf23904136ac5abefa9c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678922"
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого оператора агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор оператора.|  
|**name**|**sysname**|Имя оператора.|  
|**включен**|**tinyint**|Состояние рассылки уведомлений по предупреждениям (логическое значение). Если **1**, этот оператор может получать уведомления при появлении предупреждения.|  
|**email_address**|**Nvarchar(100)**|Адрес электронной почты оператора.|  
|**last_email_date**|**int**|Дата последнего получения оператором уведомления о предупреждении по электронной почте.|  
|**last_email_time**|**int**|Время последнего получения оператором уведомления о предупреждении по электронной почте.|  
|**pager_address**|**Nvarchar(100)**|Адрес пейджера для данного оператора.|  
|**last_pager_date**|**int**|Дата последнего получения оператором уведомления о предупреждении на пейджер.|  
|**last_pager_time**|**int**|Время последнего получения оператором уведомления о предупреждении на пейджер.|  
|**weekday_pager_start_time**|**int**|Время (с понедельника по пятницу), после которого данный оператор может получать уведомления о предупреждении, отправляемые на пейджер.|  
|**weekday_pager_end_time**|**int**|Время (с понедельника по пятницу), после которого данный оператор не может получать уведомления о предупреждении, отправляемые на пейджер.|  
|**saturday_pager_start_time**|**int**|Время (в субботу), после которого данный оператор может получать уведомления о предупреждении, отправляемые на пейджер.|  
|**saturday_pager_end_time**|**int**|Время (в субботу), после которого данный оператор не может получать уведомления о предупреждении, отправляемые на пейджер.|  
|**sunday_pager_start_time**|**int**|Время (в воскресенье), после которого данный оператор может получать уведомления о предупреждениях, отправленные на пейджер.|  
|**sunday_pager_end_time**|**int**|Время (в воскресенье), после которого данный оператор не может получать уведомления о предупреждении, отправленные на пейджер.|  
|**pager_days**|**tinyint**|Битовая маска, определяющая дни недели, во время которых оператор может получать уведомления о предупреждении, отправленные на пейджер.|  
|**netsend_address**|**Nvarchar(100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**int**|Дата отправки последнего сетевого сообщения оператору с указанным идентификатором.|  
|**last_netsend_time**|**int**|Время отправки последнего сетевого сообщения оператору с указанным идентификатором.|  
|**category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [Таблицы агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
