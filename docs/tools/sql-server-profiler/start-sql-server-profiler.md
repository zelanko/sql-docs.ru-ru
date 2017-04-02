---
title: "Запуск приложения SQL Server Profiler | Microsoft Docs"
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
  - "Profiler [SQL Server Profiler], запуск"
  - "SQL Server Profiler, запуск"
  - "запуск приложения SQL Server Profiler"
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# Запуск приложения SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно запустить несколькими способами, позволяющими получать данные трассировки в различных ситуациях. Можно запустить приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] из меню **Пуск** , из меню **Сервис** в помощнике по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и из нескольких мест в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 При первом запуске [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и выборе в меню **Файл** пункта **Создать трассировку** приложение отображает диалоговое окно **Соединение с сервером** , где можно указать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , к которому необходимо подключиться.  
  
### Запуск приложения SQL Server Profiler из меню «Пуск»  
  
1.  В меню **Пуск** последовательно укажите **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства обеспечения производительности**и выберите пункт **SQL Server Profiler**.  
  
### Запуск SQL Server Profiler в помощнике по настройке ядра СУБД  
  
1.  В меню [!INCLUDE[ssDE](../../includes/ssde-md.md)] Сервис **помощника по настройке компонента** выберите **SQL Server Profiler**.  
  
## Запуск приложения SQL Server Profiler в среде SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] запускает каждый сеанс профайлера в отдельном экземпляре, выполнение которого продолжается после завершения работы [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно запустить из нескольких мест в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], как показано в следующих процедурах. При запуске приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] загружается контекст соединения, шаблон трассировки и выполняется фильтрация контекста точки запуска.  
  
#### Запуск приложения SQL Server Profiler из меню «Инструменты»  
  
1.  В меню среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Инструменты** выберите **SQL Server Profiler**.  
  
#### Запуск приложения SQL Server Profiler из редактора запросов  
  
1.  В строке меню среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выберите пункт **Создать запрос**.  
  
2.  В редакторе запросов щелкните правой кнопкой мыши, а затем выберите пункт **Трассировка запроса в приложении SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Контекстом соединения является редактор соединения, шаблон трассировки — TSQL_SP, а применяемый фильтр SPID = окно запроса SPID.  
  
#### Запуск приложения SQL Server Profiler из монитора активности  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выберите **Монитор активности**.  
  
2.  Щелкните панель **Процессы**, щелкните правой кнопкой процесс, который хотите профилировать, а затем выберите пункт **Трассировать процесс в приложении SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Когда выбран процесс, контекстом соединения является соединение обозревателя объектов при открытии монитора активности. Шаблон трассировки — это шаблон по умолчанию в зависимости от типа сервера, а идентификатор SPID равен идентификатору SPID для выбранного процесса.  
  
## Безопасность .NET Framework  
 В режиме проверки подлинности Windows учетная запись пользователя, от имени которой запускается приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], должна иметь разрешение на соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для выполнения трассировки в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] пользователь должен также иметь разрешение ALTER TRACE.  
  
## См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Использование среды SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
  
  