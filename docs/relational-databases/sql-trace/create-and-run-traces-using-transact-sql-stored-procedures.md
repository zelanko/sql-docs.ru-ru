---
title: Создание и запуск трассировки с помощью хранимых процедур Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
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
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6ebeecb2e972023d7b1a5bdab7e654a38edf6829
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a>Создание и запуск трассировки с помощью хранимых процедур Transact-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Процесс трассировки с помощью компонента трассировки SQL зависит от того, каким образом создана и запущена трассировка: в приложении Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] или с помощью системных хранимых процедур.  
  
 Помимо компонента [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], для создания и запуска трассировок можно использовать системные хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] . Для управления процессом трассировки предусмотрены следующие системные хранимые процедуры:  
  
1.  Создание трассировки с использованием процедуры **sp_trace_create**.  
  
2.  Добавление событий с использованием процедуры **sp_trace_setevent**.  
  
3.  Настройка фильтра с использованием процедуры **sp_trace_setfilter**(необязательно).  
  
4.  Запуск трассировки с использованием процедуры **sp_trace_setstatus**.  
  
5.  Остановка трассировки с использованием процедуры **sp_trace_setstatus**.  
  
6.  Закрытие трассировки с использованием процедуры **sp_trace_setstatus**.  
  
    > [!NOTE]  
    >  Системные хранимые процедуры языка [!INCLUDE[tsql](../../includes/tsql-md.md)] создают трассировку на уровне сервера, что гарантирует сохранность всех событий при условии наличия свободного места на диске и отсутствии ошибок записи. Если диск переполняется или происходит сбой, то экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] продолжает выполняться, но трассировка прерывается. Если установлен режим аудита **c2** и происходит ошибка записи, то трассировка останавливается, а экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрывается. Дополнительные сведения о настройке **c2 audit mode** см. в разделе [Параметр конфигурации сервера c2 audit mode](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Оптимизация трассировки SQL](../../relational-databases/sql-trace/optimize-sql-trace.md)|Сведения о способах снижения воздействия трассировки на производительность системы.|  
|[Фильтрация трассировки](../../relational-databases/sql-trace/filter-a-trace.md)|Сведения о применении фильтров для трассировки.|  
|[Ограничение размеров файла и таблицы трассировки](../../relational-databases/sql-trace/limit-trace-file-and-table-sizes.md)|Сведения об ограничении размера файлов и таблиц, в которые записываются данные трассировки. Обратите внимание, что записывать данные трассировки в таблицы может только [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .|  
|[Планирование трассировок](../../relational-databases/sql-trace/schedule-traces.md)|Сведения о настройке времени начала и завершения трассировки.|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
