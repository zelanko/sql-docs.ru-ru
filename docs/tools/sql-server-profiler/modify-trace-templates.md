---
title: "Изменение шаблонов трассировки | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "шаблоны [SQL Server], SQL Server Profiler"
  - "Profiler [SQL Server Profiler], шаблоны"
  - "шаблоны трассировки [SQL Server]"
  - "изменение шаблонов трассировки"
  - "SQL Server Profiler, шаблоны"
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Изменение шаблонов трассировки
  Можно изменить шаблоны, сохраняемые в файле на локальном компьютере, на котором выполняется [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Можно также изменить шаблоны, производные от этих файлов. При изменении существующих шаблонов выполняется редактирование таких свойств шаблонов, как классы событий и столбцы данных в том же порядке, в котором эти свойства были установлены первоначально, на вкладке **Выбор событий** диалогового окна **Свойства трассировки** . Классы событий и столбцы данных можно добавлять и удалять, а фильтры изменять. После изменения шаблона создается пользовательский шаблон и исходный системный шаблон остается без изменений. Дополнительные сведения см. в разделе [Сохранение трассировок и шаблонов трассировок](../../tools/sql-server-profiler/save-traces-and-trace-templates.md).  
  
 Может потребоваться производный шаблон от существующего файла трассировки, если пользователь не помнит (или не сохранил) исходный шаблон, использованный при создании трассировки, или если нужно выполнить ту же трассировку в последующий день. При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку. Дополнительные сведения см. в разделах [Создать шаблон на основе файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) и [Создать шаблон на основе выполняемой трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **Создание шаблона трассировки**  
  
 [Создание шаблона трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
 **Запуск трассировки из шаблона**  
  
 [Создание трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 **Изменение шаблона трассировки**  
  
 [Использование приложения SQL Server Profiler](../../tools/sql-server-profiler/modify-a-trace-template-sql-server-profiler.md)  
  
 [Использование Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **Добавление и удаление событий из шаблона трассировки или файла трассировки**  
  
 [Использование приложения SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Использование Transact-SQL](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
## См. также:  
 [Запуск трассировки](../../tools/sql-server-profiler/start-a-trace.md)  
  
  