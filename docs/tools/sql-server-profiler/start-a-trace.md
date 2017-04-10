---
title: "Запуск трассировки | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Profiler, остановка трассировок"
  - "приостановка трассировок"
  - "Profiler [SQL Server Profiler], остановка трассировок"
  - "Profiler [SQL Server Profiler], запуск трассировок"
  - "трассировки [SQL Server], запуск"
  - "SQL Server Profiler, приостановка трассировок"
  - "трассировки [SQL Server], остановка"
  - "Profiler [SQL Server Profiler], приостановка трассировок"
  - "трассировки [SQL Server], приостановка"
  - "SQL Server Profiler, запуск трассировок"
  - "остановка трассировок"
  - "запуск трассировок"
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Запуск трассировки
  После определения новой трассировки или создания шаблона при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно запускать, приостанавливать или останавливать сбор данных, используя новое определение трассировки или новый шаблон.  
  
## Запуск трассировки  
 Когда запускается трассировка, а определенным источником является экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] или служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает очередь, служащую для временного хранения данных о зарегистрированных серверных событиях.  
  
 При обращении к инструменту трассировки SQL посредством приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] открывается новое окно трассировки (если ни одно такое окно еще не открыто) и немедленно выполняется регистрация данных.  
  
 Если обращение следует к механизму трассировки SQL с использованием системных хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)], трассировку нужно запускать каждый раз, когда экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинает регистрацию данных. После запуска трассировки можно изменить только ее имя.  
  
> [!NOTE]  
>  При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку.  
  
## См. также:  
 [Автоматически запустить трассировку после соединения с сервером (приложение SQL Server Profiler)](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Приостановить трассировку (приложение SQL Server Profiler)](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   
 [Остановить трассировку (приложение SQL Server Profiler)](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   
 [Очистить окно трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   
 [Провести трассировку после ее приостановки или прекращения (приложение SQL Server Profiler)](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  