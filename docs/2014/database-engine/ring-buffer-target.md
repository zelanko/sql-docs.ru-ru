---
title: Целевой буфер кольца | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbba7b6da37f292d31d985921d25be5cabc51798
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193228"
---
# <a name="ring-buffer-target"></a>Цель «Кольцевой буфер»
  Цель «Кольцевой буфер» кратковременно хранит данные о событиях в памяти. Данная цель может управлять событиями в одном из двух режимов.  
  
-   Первый режим — это режим, «первым поступил — первым обслужен» (FIFO), когда при заполнении всей памяти, выделенной цели, теряется событие, которое было добавлено первым. В данном режиме (режим по умолчанию) для параметра occurrence_number задается значение 0.  
  
-   Второй режим — это режим FIFO по видам событий, в котором хранится только определенное число событий каждого типа. В этом режиме при заполнении всей памяти, выделенной цели, удаляются самые старые события каждого типа. Параметр occurrence_number можно изменить, чтобы указать количество событий каждого типа, которые следует сохранять.  
  
 В следующей таблице приведены доступные параметры для настройки цели «Кольцевой буфер».  
  
|Параметр|Допустимые значения|Описание|  
|------------|--------------------|-----------------|  
|max_memory|Любое 32-разрядное целое число. Это значение является необязательным.|Максимальный объем памяти в килобайтах (КБ), который будет использован. Существующие события удаляются в соответствии с первым достигнутым ограничением — max_event_limit или max_memory.|  
|max_event_limit|Любое 32-разрядное целое число. Это значение является необязательным.|Максимальное количество событий, которые хранятся в ring_buffer. Существующие события удаляются в соответствии с первым достигнутым ограничением — max_event_limit или max_memory. По умолчанию — 1000.|  
|occurrence_number|Одно из следующих значений:<br /><br /> 0 (по умолчанию) — если вся выделенная цели память использована, то самое старое событие удаляется.<br /><br /> Любое 32-разрядное целое число — количество событий каждого типа, которое следует хранить до удаления в режиме FIFO для каждого события.<br /><br /> <br /><br /> Это значение является необязательным.|Режим FIFO, который будет применяться, а также (в случае если установлено значение больше 0) предпочитаемое число событий каждого типа, которые следует сохранять в буфере.|
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

- [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md)
- [sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [ALTER EVENT SESSION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

