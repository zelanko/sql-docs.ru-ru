---
title: Запуск SQL Server Profiler | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a3219168a070a9c264d4fb5457f9e5844734844a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68186116"
---
# <a name="start-sql-server-profiler"></a>Запуск приложения SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно запустить несколькими способами, позволяющими получать данные трассировки в различных ситуациях. Можно запустить приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] из меню **Пуск** , из меню **Сервис** в помощнике по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и из нескольких мест в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 При первом запуске [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и выборе в меню **Файл** пункта **Создать трассировку** приложение отображает диалоговое окно **Соединение с сервером** , где можно указать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , к которому необходимо подключиться.  
  
### <a name="to-start-sql-server-profiler-from-the-start-menu"></a>Запуск приложения SQL Server Profiler из меню «Пуск»  
  
1.  В меню **Пуск** последовательно укажите **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства обеспечения производительности**и выберите пункт **SQL Server Profiler**.  
  
### <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Запуск SQL Server Profiler в помощнике по настройке ядра СУБД  
  
1.  В меню [!INCLUDE[ssDE](../../includes/ssde-md.md)] Сервис **помощника по настройке компонента** выберите **SQL Server Profiler**.  
  
## <a name="starting-sql-server-profiler-in-management-studio"></a>Запуск приложения SQL Server Profiler в среде SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] запускает каждый сеанс профайлера в отдельном экземпляре, выполнение которого продолжается после завершения работы [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно запустить из нескольких мест в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], как показано в следующих процедурах. При запуске приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] загружается контекст соединения, шаблон трассировки и выполняется фильтрация контекста точки запуска.  
  
#### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Запуск приложения SQL Server Profiler из меню «Инструменты»  
  
1.  В меню среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Инструменты** выберите **SQL Server Profiler**.  
  
#### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Запуск приложения SQL Server Profiler из редактора запросов  
  
1.  В строке меню среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] выберите пункт **Создать запрос**.  
  
2.  В редакторе запросов щелкните правой кнопкой мыши, а затем выберите пункт **Трассировка запроса в приложении SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Контекстом соединения является редактор соединения, шаблон трассировки — TSQL_SP, а применяемый фильтр SPID = окно запроса SPID.  
  
#### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Запуск приложения SQL Server Profiler из монитора активности  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и выберите **Монитор активности**.  
  
2.  Щелкните панель **Процессы** , щелкните правой кнопкой процесс, который хотите профилировать, а затем выберите пункт **Трассировать процесс в приложении SQL Server Profiler**.  
  
    > [!NOTE]  
    >  Когда выбран процесс, контекстом соединения является соединение обозревателя объектов при открытии монитора активности. Шаблон трассировки — это шаблон по умолчанию в зависимости от типа сервера, а идентификатор SPID равен идентификатору SPID для выбранного процесса.  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 В режиме проверки подлинности Windows учетная запись пользователя, от имени которой запускается приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , должна иметь разрешение на соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для выполнения трассировки в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]пользователь должен также иметь разрешение ALTER TRACE.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)   
 [Использование среды SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)  
  
  
