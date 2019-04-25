---
title: dbo.sysalerts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7bad6fbd9229547318a060f08eeb102b21cda9bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470892"
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
|**include_event_description**|**tinyint**|Битовая маска, определяющая ли описание события отправляется по электронной почте, пейджеру или команды Net send. См. ниже приведены значения.|  
|**database_name**|**nvarchar(512)**|База данных, в которой должно произойти предупреждение, чтобы оно сработало.|  
|**event_description_keyword**|**nvarchar(100)**|Шаблон, с которым должна совпасть ошибка для срабатывания этого предупреждения.|  
|**occurrence_count**|**int**|Количество раз, когда возникало этого предупреждение.|  
|**count_reset_date**|**int**|Число дней (дата) будет сброшен на **0**.|  
|**count_reset_time**|**int**|Время дня счетчик будет сброшен на **0**.|  
|**job_id**|**uniqueidentifier**|Идентификатор задачи, выполняемой, когда происходит предупреждение.|  
|**has_notification**|**int**|Количество операторов, получающих при возникновении предупреждения уведомление по электронной почте.|  
|**flags**|**int**|Зарезервировано.|  
|**performance_condition**|**nvarchar(512)**|Зарезервировано.|  
|**category_id**|**int**|Зарезервировано.|  
  
 ## <a name="remarks"></a>Примечания

В следующей таблице показаны значения битовой маски include_event_description. Dbo.sysalerts возвращает десятичное значение. 

|Decimal | binary | Значение |
|------|------|------|
|0 |0000 |сообщение не |
|1 |0001 |Отправить по электронной почте |
|2 |0010 |пейджер |
|3 |0011 |пейджера и адрес электронной почты |
|4 |0100 |Net send |
|5 |0101 |Команда net send и адрес электронной почты |
|6 |0110 |Команда net send и на пейджер |
|7 |0111 |Команда net send, пейджер и электронной почты |
  
