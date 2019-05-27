---
title: Цели счетчика событий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ddf153da7af2906fe7167c8cb2b77d9100d1154f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66064922"
---
# <a name="event-counter-target"></a>Цель счетчика событий
  Целью счетчика событий являются все события, возникающие в ходе сеанса расширенных событий. С помощью цели счетчика событий вы можете получать сведения о характеристиках рабочей нагрузки без затрат на сбор всех событий. У этой цели нет настраиваемых параметров.  
  
## <a name="adding-the-target-to-a-session"></a>Добавление цели к сеансу  
 Для добавления цели счетчика событий в сеанс расширенных событий следует использовать одну из следующих инструкций при создании или изменении сеанса события:  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a>Просмотр целевого вывода  
 Для просмотра результата цели счетчика событий можно воспользоваться следующим запросом, заменив параметр *session_name* на имя сеанса события:  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 В следующем примере показан формат выходных данных цели счетчика событий.  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a>См. также  
 [Цели расширенных событий SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
