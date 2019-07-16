---
title: sys.dm_xe_sessions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_sessions_TSQL
- dm_xe_sessions
- sys.dm_xe_sessions_TSQL
- sys.dm_xe_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_sessions dynamic management view
- extended events [SQL Server], views
ms.assetid: defd6efb-9507-4247-a91f-dc6ff5841e17
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b42a6808d9cab6a3431a68bff9e29e83354a2af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090226"
---
# <a name="sysdmxesessions-transact-sql"></a>sys.dm_xe_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об активном сеансе расширенных событий. Этот сеанс представляет собой коллекцию событий, действий и целей.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|address|**varbinary(8)**|Адрес памяти сеанса. адрес является уникальным в локальной системе. Не допускает значение NULL.|  
|name|**nvarchar(256)**|Имя сеанса. имя является уникальным в локальной системе. Не допускает значение NULL.|  
|pending_buffers|**int**|Число полных буферов, ожидающих обработки. Не допускает значение NULL.|  
|total_regular_buffers|**int**|Общее число обычных буферов, связанных с сеансом. Не допускает значение NULL.<br /><br /> Примечание. В большинстве случаев используются обычные буферы. Размер этих буферов достаточен для размещения многих событий. Обычно в сеансе будут использоваться три или более буферов. Число обычных буферов определяется сервером автоматически, основываясь на секционировании памяти, заданном через параметр MEMORY_PARTITION_MODE. Размер обычных буферов равен значению параметра MAX_MEMORY (значение по умолчанию = 4 Мб), разделенному на число буферов. Дополнительные сведения о MEMORY_PARTITION_MODE и MAX_MEMORY параметрах см. в разделе [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md).|  
|regular_buffer_size|**bigint**|Размер обычного буфера в байтах. Не допускает значение NULL.|  
|total_large_buffers|**int**|Общее число больших буферов. Не допускает значение NULL.<br /><br /> Примечание. Большие буферы используются в том случае, когда событие больше обычного буфера. Они выделяются специально в этих целях. Большие буферы выделяются в начале сеанса события, их размер определяется параметром MAX_EVENT_SIZE. Дополнительные сведения о параметре max_event_size см. в разделе [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md).|  
|large_buffer_size|**bigint**|Размер большого буфера в байтах. Не допускает значение NULL.|  
|total_buffer_size|**bigint**|Общий размер буфера памяти, использованного для хранения событий для сеанса (в байтах). Не допускает значение NULL.|  
|buffer_policy_flags|**int**|Битовая карта, которая показывает поведение буферов событий сеанса в том случае, когда все буферы полны и происходит новое событие. Не допускает значение NULL.|  
|buffer_policy_desc|**nvarchar(256)**|Описание, которое показывает поведение буферов событий сеанса в случае, когда все буферы полны и происходит новое событие.  Не допускает значение NULL. buffer_policy_desc может принимать одно из следующих значений:<br /><br /> Удалить событие<br /><br /> Не удалять события<br /><br /> Удалить полный буфер<br /><br /> Выделить новый буфер|  
|flags|**int**|Битовая карта, которая указывает флаги, установленные для сеанса. Не допускает значение NULL.|  
|flag_desc|**nvarchar(256)**|Описание флагов, установленных для сеанса.  Не допускает значение NULL. flag_desc может быть любым сочетанием следующих:<br /><br /> Записать буферы при закрытии<br /><br /> Выделенный диспетчер<br /><br /> Разрешить рекурсивные события|  
|dropped_event_count|**int**|Число событий, удаленных, когда буфер был полон. Это значение равно **0** Если политика буфера — «Удалить полный буфер» или «Не удалять события». Не допускает значение NULL.|  
|dropped_buffer_count|**int**|Число буферов, удаленных, когда буферы были полными. Это значение равно **0** Если политика буфера имеет значение «Удалить событие» или «Не удалять события». Не допускает значение NULL.|  
|blocked_event_fire_time|**int**|Длительность времени, в течение которого происходившие события были блокированы при полных буферах. Это значение равно **0** Если политика буфера — «Удалить полный буфер» или «Удалить событие». Не допускает значение NULL.|  
|create_time|**datetime**|Время создания сеанса. Не допускает значение NULL.|  
|largest_event_dropped_size|**int**|Размер самого крупного события, которое не уместилось в буфере сеанса. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

