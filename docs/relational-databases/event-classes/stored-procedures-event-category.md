---
title: Категория событий Stored Procedures | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c88932cd800e5956a0ab0bbd34e5d25ce222a0fd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stored-procedures-event-category"></a>Категория событий Stored Procedures
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Категория событий **Stored Procedures** содержит общие события хранимых процедур.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий RPC:Completed](../../relational-databases/event-classes/rpc-completed-event-class.md)|Указывает на завершение удаленного вызова процедуры (RPC).|  
|[Класс событий PreConnect:Completed](../../relational-databases/event-classes/preconnect-completed-event-class.md)|Указывает, что функция-классификатор регулятора ресурсов завершает выполнение.|  
|[PreConnect:Starting, класс событий](../../relational-databases/event-classes/preconnect-starting-event-class.md)|Указывает, что запускается функция-классификатор регулятора ресурсов.|  
|[Класс событий RPC Output Parameter](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)|Отслеживает выходные значения параметров удаленного вызова процедуры после выполнения.|  
|[Класс событий RPC:Starting](../../relational-databases/event-classes/rpc-starting-event-class.md)|Указывает на начало удаленного вызова процедуры.|  
|[Класс событий SP:CacheHit](../../relational-databases/event-classes/sp-cachehit-event-class.md)|Указывает, что хранимая процедура хранится в кэше.|  
|[Класс событий SP:CacheInsert](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)|Указывает, что хранимая процедура была помещена в кэш.|  
|[Класс событий SP:CacheMiss](../../relational-databases/event-classes/sp-cachemiss-event-class.md)|Указывает, что хранимую процедуру не удалось найти в кэше.|  
|[Класс событий SP:CacheRemove](../../relational-databases/event-classes/sp-cacheremove-event-class.md)|Указывает, что хранимая процедура была удалена из кэша.|  
|[Класс событий SP:Completed](../../relational-databases/event-classes/sp-completed-event-class.md)|Указывает, что выполнение хранимой процедуры завершено.|  
|[Класс событий SP:Recompile](../../relational-databases/event-classes/sp-recompile-event-class.md)|Указывает, что осуществляется повторная компиляция хранимой процедуры.|  
|[Класс событий SP:Starting](../../relational-databases/event-classes/sp-starting-event-class.md)|Указывает на начало выполнения хранимой процедуры.|  
|[Класс событий SP:StmtCompleted](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)|Указывает, что завершено выполнение инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимой процедуре.|  
|[Класс событий SP:StmtStarting](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|Указывает на начало выполнения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимой процедуре.|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
