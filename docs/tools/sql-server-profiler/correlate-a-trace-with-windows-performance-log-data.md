---
title: "Сопоставление трассировки с журналом производительности Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сопоставление трассировки с данными журнала"
  - "журналы [SQL Server], трассировки"
  - "Profiler [SQL Server Profiler], сопоставление трассировки с данными журнала"
  - "трассировки [SQL Server], журналы"
  - "SQL Server Profile, сопоставление трассировки с данными журнала"
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Сопоставление трассировки с журналом производительности Windows
  С помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно открыть журнал производительности Microsoft Windows, выбрать счетчики, которые нужно сопоставить с трассировкой, и отобразить выбранные счетчики производительности рядом с трассировкой в графическом пользовательском интерфейсе приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . При выборе события в окне трассировки вертикальная красная линия на панели окна системного монитора в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] показывает данные журнала производительности, которые сопоставлены выбранному событию трассировки.  
  
 Чтобы сопоставить трассировку со счетчиками производительности, откройте файл трассировки или таблицу, содержащую столбцы данных **Начальное время** и **Конечное время** data columns, и then click **Импортировать данные производительности** в меню приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Файл** . Потом можно открыть журнал производительности и выбрать объекты системного монитора и счетчики, которые сопоставляются с трассировкой.  
  
## См. также:  
 [Сопоставление трассировки с журналом производительности Windows (приложение SQL Server Profiler)](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  