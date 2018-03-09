---
title: "dbo.sysalerts (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysalerts
- sysalerts_TSQL
- dbo.sysalerts_TSQL
- sysalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysalerts system table
ms.assetid: a2c2f50d-61f3-4951-996a-add5ad092cc2
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7565ee20e5fdec3a94c413b8204629ce6ee2f48d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysalerts-transact-sql"></a>dbo.sysalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого предупреждения. Предупреждение — это сообщение, отправляемое как реакция на событие. Предупреждения могут направлять сообщения не только в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, предупреждение может быть сообщением электронной почты или пейджера. Предупреждения также могут создавать задачи.  Эта таблица хранится в **msdb** базы данных.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор предупреждения.|  
|**name**|**sysname**|Имя предупреждения.|  
|**event_source**|**nvarchar(100)**|Источник события: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**event_category_id**|**int**|Зарезервировано для последующего использования.|  
|**event_id**|**int**|Зарезервировано для последующего использования.|  
|**message_id**|**int**|Определяемые пользователем идентификатор сообщения или ссылка на **sysmessages** сообщение, вызвавшее это предупреждение.|  
|**severity**|**int**|Серьезность события, вызвавшего это предупреждение.|  
|**включен**|**tinyint**|Состояние предупреждения:<br /><br /> **0** = отключено.<br /><br /> **1** = включен.|  
|**delay_between_responses**|**int**|Время ожидания между отправкой уведомлений для этого предупреждения (в секундах).|  
|**last_occurrence_date**|**int**|Дата последнего возникновения предупреждения.|  
|**last_occurrence_time**|**int**|Время последнего возникновения предупреждения.|  
|**last_response_date**|**int**|Дата последней отправки предупреждения.|  
|**last_response_time**|**int**|Время последней отправки предупреждения.|  
|**notification_message**|**nvarchar(512)**|Дополнительные сведения, отправляемые вместе с предупреждением.|  
|**include_event_description**|**tinyint**|Битовая маска, определяющая ли описание события отправляется по электронной почте, пейджеру или команды Net send. См. диаграмму ниже значений.|  
|**database_name**|**nvarchar(512)**|База данных, в которой должно произойти предупреждение, чтобы оно сработало.|  
|**event_description_keyword**|**nvarchar(100)**|Шаблон, с которым должна совпасть ошибка для срабатывания этого предупреждения.|  
|**occurrence_count**|**int**|Количество раз, когда возникало этого предупреждение.|  
|**count_reset_date**|**int**|Число дней (date) будут сброшены **0**.|  
|**count_reset_time**|**int**|Время суток количество будут сброшены **0**.|  
|**job_id**|**uniqueidentifier**|Идентификатор задачи, выполняемой, когда происходит предупреждение.|  
|**has_notification**|**int**|Количество операторов, получающих при возникновении предупреждения уведомление по электронной почте.|  
|**flags**|**int**|Зарезервировано.|  
|**performance_condition**|**nvarchar(512)**|Зарезервировано.|  
|**category_id**|**int**|Зарезервировано.|  
  
 ## <a name="remarks"></a>Remarks

В следующей таблице показаны значения битовой маски include_event_description. Десятичное значение возвращается dbo.sysalerts. 

|Decimal | BINARY | Значение |
|------|------|------|
|0 |0000 |сообщение не |
|1 |0001 |Отправить по электронной почте |
|2 |0010 |пейджер |
|3 |0011 |пейджера и адрес электронной почты |
|4 |0100 |Net send |
|5 |0101 |Net send и электронной почты |
|6 |0110 |Команды net send и на пейджер |
|7 |0111 |Команды net send, пейджер и электронной почты |
  
