---
title: Изменение существующей трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: sql-trace
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39dcdd0347e21b7975de3e75b84492685a04f487
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="modify-an-existing-trace-transact-sql"></a>изменить существующую трассировку (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
