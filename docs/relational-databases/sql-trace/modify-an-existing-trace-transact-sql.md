---
title: Изменение существующей трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 63f41914062a0f5153c95cba7a710745edf350ac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746152"
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
  
  
