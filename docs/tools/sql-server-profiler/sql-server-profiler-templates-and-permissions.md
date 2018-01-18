---
title: "Шаблоны приложения SQL Server Profiler и разрешения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
caps.latest.revision: "34"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fe9d9cbe084c3e721f41ab6f0546c6cf52b9fe1a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-profiler-templates-and-permissions"></a>Шаблоны и разрешения приложения SQL Server Profiler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] показано, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет внутреннее разрешение запросов. Благодаря этому администраторы могут точно узнать, какие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] или многомерные выражения передаются на сервер и как он обращается к базе данных или кубу, чтобы сформировать результирующий набор.  
  
 Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]позволяет:  
  
-   создать трассировку на основе многоразового шаблона;  
  
-   наблюдать результаты трассировки во время ее работы;  
  
-   сохранять результаты трассировки в таблицу;  
  
-   запускать, останавливать, приостанавливать и изменять результаты трассировки по мере необходимости;  
  
-   воспроизводить результаты трассировки.  
  
 Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет наблюдать только за нужными событиями. Если трассировки становятся слишком большими, их можно отфильтровать так, чтобы собирались только необходимые сведения. Мониторинг слишком большого потока событий может привести к перегрузке сервера и процесса трассировки, кроме того, файл или таблица трассировки могут вырасти до огромных размеров, особенно если процесс наблюдения ведется в течение долгого периода времени.  
  
> [!NOTE]  
>  Значения столбца трассировки, имеющие размер больше 1 ГБ, вызывают ошибку и усекаются в выводе трассировки.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Шаблоны приложения SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates.md)|Содержит сведения о предопределенных шаблонах трассировки, которые входят в состав приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Разрешения, необходимые для запуска приложения SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)|Содержит сведения о разрешениях, которые требуются для работы с приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Сохранение трассировок и шаблонов трассировок](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)|Содержит сведения о сохранении результатов трассировки и сохранении определений трассировки в виде шаблона.|  
|[Изменение шаблонов трассировки](../../tools/sql-server-profiler/modify-trace-templates.md)|Содержит сведения об изменении шаблонов трассировки при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] или инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Запуск трассировки](../../tools/sql-server-profiler/start-a-trace.md)|Содержит сведения о том, что происходит при запуске, приостановке или завершении трассировки.|  
|[Сопоставление трассировки с журналом производительности Windows](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)|Содержит сведения о проверке корреляции данных журнала производительности Windows с трассировкой при помощи приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Просмотр и анализ трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)|Содержит сведения об использовании трассировки для устранения неполадок, отображении имен и поиске событий в трассировке.|  
|[Анализ взаимоблокировок в приложении SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)|Содержит сведения об использовании приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для определения причины возникновения взаимоблокировки.|  
|[Анализ запросов с помощью результатов инструкции SHOWPLAN в приложении SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)|Содержит сведения об использовании приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для сбора и отображения результатов инструкций Showplan и Showplan Statistics.|  
|[Фильтрация трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md)|Содержит сведения о настройке фильтров по столбцам данных для фильтрации результатов трассировки с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)|Содержит описание процесса воспроизведения трассировки и требования, которые к нему предъявляются.|  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Запуск приложения SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
