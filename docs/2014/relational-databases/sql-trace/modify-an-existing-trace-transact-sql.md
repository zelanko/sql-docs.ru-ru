---
title: Изменение существующей трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68d98a838fb17360997d7eb4a1db025176e322aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168285"
---
# <a name="modify-an-existing-trace-transact-sql"></a>изменить существующую трассировку (Transact-SQL)
  В этом подразделе описано, как при помощи хранимых процедур изменить существующую трассировку.  
  
### <a name="to-modify-an-existing-trace"></a>Изменение существующей трассировки  
  
1.  Чтобы остановить трассировку, если она уже выполняется, выполните процедуру **sp_trace_setstatus** , указав параметр **@status =0**.  
  
2.  Чтобы изменить события трассировки, выполните процедуру **sp_trace_setevent** , указав изменения с помощью параметров. Эти параметры перечислены ниже (по порядку):  
  
    -   **@traceid** (идентификатор трассировки)  
  
    -   **@eventid** (идентификатор события)  
  
    -   **@columnid** (идентификатор столбца)  
  
    -   **@on** (ON)  
  
     При изменении значения параметра **@on** необходимо помнить о том, как он взаимодействует с параметром **@columnid** .  
  
    |ON|Идентификатор столбца|Результат|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|Событие включено. Все столбцы очищены.|  
    ||NOT NULL|Столбец включен для указанного события.|  
    |OFF (**0**)|NULL|Событие выключено. Все столбцы очищены.|  
    ||NOT NULL|Столбец выключен для указанного события.|  
  
> [!IMPORTANT]  
>  Параметры всех хранимых процедур [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (**sp_trace_* xx***), в отличие от обычных хранимых процедур, жестко типизированы и не поддерживают автоматическое преобразование типов данных. Если эти параметры не вызываются вместе с правильными типами данных входных параметров, как указано в описании аргумента, хранимая процедура возвращает ошибку.  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_trace_setstatus (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Системные хранимые процедуры (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
