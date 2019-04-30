---
title: Создание фильтра трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6e3ecc4b125d226fc2cdf6dbe241e0ce017eae6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63245937"
---
# <a name="set-a-trace-filter-transact-sql"></a>создать фильтр трассировки (Transact-SQL)
  В этом разделе описывается, как использовать хранимые процедуры для создания фильтра, который возвращает только данные, необходимые для трассируемого события.  
  
### <a name="to-set-a-trace-filter"></a>Установка фильтра трассировки  
  
1.  Чтобы остановить трассировку, если она уже выполняется, выполните процедуру **sp_trace_setstatus** , указав параметр **@status =0**.  
  
2.  Выполните хранимую процедуру **sp_trace_setfilter** , чтобы определить тип данных, которые необходимо получить для трассируемого события.  
  
> [!IMPORTANT]
>  Параметры всех хранимых процедур [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (<strong>sp_trace_*xx*</strong>), в отличие от обычных хранимых процедур, жестко типизированы и не поддерживают автоматическое преобразование типов данных. Если эти аргументы указываются с неправильными типами данных входных параметров, как указано в описании их аргументов, хранимая процедура возвратит ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Фильтрация трассировки](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)   
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Системные хранимые процедуры (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
