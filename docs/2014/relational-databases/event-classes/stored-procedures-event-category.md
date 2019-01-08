---
title: Категория событий Stored Procedures | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47dc8180fd6c8f59050520477724ff8adbc46a6a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795006"
---
# <a name="stored-procedures-event-category"></a>Категория событий Stored Procedures
  Категория событий **Stored Procedures** содержит общие события хранимых процедур.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий RPC:Completed](rpc-completed-event-class.md)|Указывает на завершение удаленного вызова процедуры (RPC).|  
|[Класс событий PreConnect:Completed](preconnect-completed-event-class.md)|Указывает, что функция-классификатор регулятора ресурсов завершает выполнение.|  
|[PreConnect:Starting, класс событий](preconnect-starting-event-class.md)|Указывает, что запускается функция-классификатор регулятора ресурсов.|  
|[Класс событий RPC Output Parameter](rpc-output-parameter-event-class.md)|Отслеживает выходные значения параметров удаленного вызова процедуры после выполнения.|  
|[Класс событий RPC:Starting](rpc-starting-event-class.md)|Указывает на начало удаленного вызова процедуры.|  
|[Класс событий SP:CacheHit](sp-cachehit-event-class.md)|Указывает, что хранимая процедура хранится в кэше.|  
|[Класс событий SP:CacheInsert](sp-cacheinsert-event-class.md)|Указывает, что хранимая процедура была помещена в кэш.|  
|[Класс событий SP:CacheMiss](sp-cachemiss-event-class.md)|Указывает, что хранимую процедуру не удалось найти в кэше.|  
|[Класс событий SP:CacheRemove](sp-cacheremove-event-class.md)|Указывает, что хранимая процедура была удалена из кэша.|  
|[Класс событий SP:Completed](sp-completed-event-class.md)|Указывает, что выполнение хранимой процедуры завершено.|  
|[Класс событий SP:Recompile](sp-recompile-event-class.md)|Указывает, что осуществляется повторная компиляция хранимой процедуры.|  
|[Класс событий SP:Starting](sp-starting-event-class.md)|Указывает на начало выполнения хранимой процедуры.|  
|[Класс событий SP:StmtCompleted](sp-stmtcompleted-event-class.md)|Указывает, что завершено выполнение инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимой процедуре.|  
|[Класс событий SP:StmtStarting](sp-stmtstarting-event-class.md)|Указывает на начало выполнения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в хранимой процедуре.|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
