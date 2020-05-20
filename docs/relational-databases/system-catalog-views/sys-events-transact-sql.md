---
title: sys. Events (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.events_TSQL
- sys.events
- events_TSQL
- events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.events catalog view
ms.assetid: f245a97a-80fc-43fb-a6e4-139420c9a47a
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 17c8ab2013a1ad36d298039c5706bd518765dd3b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831976"
---
# <a name="sysevents-transact-sql"></a>sys.events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого события, для которого срабатывает триггер или уведомление о событии. Эти события представляют типы событий, которые указываются при создании триггера или уведомления о событии с помощью команды [создать триггер](../../t-sql/statements/create-trigger-transact-sql.md) или [создать уведомление о событии](../../t-sql/statements/create-event-notification-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор триггера или уведомления о событии. Это значение вместе с **типом**уникально идентифицирует строку.|  
|**type**|**int**|Событие, которое возникает при срабатывании триггера.|  
|**type_desc**|**nvarchar(60)**|Описание события, которое возникает при срабатывании триггера.|  
|**is_trigger_event**|**bit**|1 = событие триггера.<br /><br /> 0 = событие уведомления.|  
|**event_group_type**|**int**|Группа событий, для которой создается уведомление о триггере или событии, или значение NULL, если уведомления для группы событий не создаются.|  
|**event_group_type_desc**|**nvarchar(60)**|Описание группы событий, для которой создается уведомление о триггере или событии, или значение NULL, если уведомления для группы событий не создаются.|  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
