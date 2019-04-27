---
title: Кольцевой буфер целевой | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d042ef49a82d16eb33cb27d80c8083a68ea69092
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773682"
---
# <a name="ring-buffer-target"></a>Цель «Кольцевой буфер»
  Цель «Кольцевой буфер» кратковременно хранит данные о событиях в памяти. Данная цель может управлять событиями в одном из двух режимов.  
  
-   Первый режим — это режим, «первым поступил — первым обслужен» (FIFO), когда при заполнении всей памяти, выделенной цели, теряется событие, которое было добавлено первым. В данном режиме (режим по умолчанию) для параметра occurrence_number задается значение 0.  
  
-   Второй режим — это режим FIFO по видам событий, в котором хранится только определенное число событий каждого типа. В этом режиме при использовании всей памяти, выделенной цели, удаляются старые события каждого типа. Параметр occurrence_number можно изменить, чтобы указать количество событий каждого типа, которые следует сохранять.  
  
 В следующей таблице приведены доступные параметры для настройки цели «Кольцевой буфер».  
  
|Параметр|Допустимые значения|Описание|  
|------------|--------------------|-----------------|  
|max_memory|Любое 32-разрядное целое число. Это значение является необязательным.|Максимальный объем памяти в килобайтах (КБ), который будет использован. Существующие события удаляются в соответствии с первым достигнутым ограничением — max_event_limit или max_memory. Максимальное значение — 4194303 КБ. Тщательного анализа необходимо сделать до задании размера буфера кольца лимиты ГБ, как это может повлиять на других потребителей памяти в SQL Server|  
|max_event_limit|Любое 32-разрядное целое число. Это значение является необязательным.|Максимальное количество событий, которые хранятся в ring_buffer. Существующие события удаляются в соответствии с первым достигнутым ограничением — max_event_limit или max_memory. По умолчанию — 1000.|  
|occurrence_number|Одно из следующих значений:<br /><br /> 0 (по умолчанию) — если вся выделенная цели память использована, то самое старое событие удаляется.<br /><br /> Любое 32-разрядное целое число — количество событий каждого типа, чтобы сохранить уничтожается по принципу FIFO-event.<br /><br /> <br /><br /> Это значение является необязательным.|Режим FIFO, который будет применяться, а также (в случае если установлено значение больше 0) предпочитаемое число событий каждого типа, которые следует сохранять в буфере.|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a>Добавление цели к сеансу  
 Для добавления цели «Кольцевой буфер» в сеанс расширенных событий следует использовать одну из следующих инструкций при создании или изменении сеанса события.  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a>Просмотр целевого вывода  
 Для просмотра результата цели "Кольцевой буфер" можно воспользоваться следующим запросом, заменив параметр *session_name* именем сеанса события.  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 В следующем примере показан выходной формат цели «Кольцевой буфер».  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a>См. также

- [Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)
- [sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [ALTER EVENT SESSION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

