---
title: "Запустите приложение SQL Server Profiler | Документы Microsoft"
ms.custom: 
ms.date: 7/7/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9ce18e13fa735921846ea7f564ff53983d0c2dca
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="run-sql-server-profiler"></a>Выполнение приложения SQL Server Profiler
  Можно запустить [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] несколькими различными способами, позволяющими получать трассировки выходные данные в различных сценариях. Можно запустить [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] из Windows 10 **запустить** меню из **средства** меню в [!INCLUDE[ssDE](../../includes/ssde-md.md)] по настройке ядра СУБД и из нескольких мест в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
При первом запуске [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и выберите **новую трассировку** из **файл** меню, приложение отображает **соединение с сервером** диалоговое окно «», где можно указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр для подключения.  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Запуск приложения SQL Server Profiler из меню Пуск Windows 10  
-  Щелкните Windows **запустить** или нажмите клавишу Windows ключа и начните вводить «SQL Server Profiler 17». Когда **SQL Server Profiler 17** плитки, щелкните ее.   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Запуск SQL Server Profiler в помощнике по настройке ядра СУБД  
-  В меню [!INCLUDE[ssDE](../../includes/ssde-md.md)] Сервис **помощника по настройке компонента** выберите **SQL Server Profiler**.  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>Запуск приложения SQL Server Profiler в SQL Server Management Studio  
 Можно запустить [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] из нескольких мест в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Когда [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] запускается, он загружается контекст соединения, шаблон трассировки и фильтрация контекста точки запуска. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]запускает каждый сеанс профайлера SQL Server в отдельном экземпляре, а профилировщик продолжается при завершении работы [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Запуск приложения SQL Server Profiler из меню «Инструменты»  
-  В меню среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Инструменты** выберите **SQL Server Profiler**.  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Запуск приложения SQL Server Profiler из редактора запросов  
- В редакторе запросов щелкните правой кнопкой мыши, а затем выберите пункт **Трассировка запроса в приложении SQL Server Profiler**.  

  > [!NOTE]  
  >  Контекстом соединения является редактор соединения, шаблон трассировки — TSQL_SP, а применяемый фильтр SPID = окно запроса SPID.  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Запуск приложения SQL Server Profiler из монитора активности  
- В мониторе активности щелкните **процессов** панели, щелкните правой кнопкой мыши процесс, который вы хотите профилировать, а затем нажмите кнопку **трассировка процесса в приложении SQL Server Profiler**.  

    > [!NOTE]  
    >  Когда выбран процесс, контекстом соединения является соединение обозревателя объектов при открытии монитора активности. Шаблон трассировки — это шаблон по умолчанию в зависимости от типа сервера, а идентификатор SPID равен идентификатору SPID для выбранного процесса.  
    
## <a name="net-framework-security"></a>Безопасность .NET Framework  
- В режиме проверки подлинности Windows учетная запись пользователя, которое будет выполняться [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] должен иметь разрешение на подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
- Для выполнения трассировки в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]пользователь должен также иметь разрешение ALTER TRACE.  

## <a name="next-steps"></a>Следующие шаги  
 [Общие сведения о SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Использование среды SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  

