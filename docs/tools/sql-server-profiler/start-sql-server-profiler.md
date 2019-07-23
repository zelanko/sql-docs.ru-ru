---
title: Запустить SQL Server Profiler | Документация Майкрософт
ms.custom: ''
ms.date: 07/07/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 697905061bb60e91884d8844a103ba1302c5c4ca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059622"
---
# <a name="run-sql-server-profiler"></a>Выполнение приложения SQL Server Profiler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] можно запустить несколькими способами для получения данных трассировки в разных сценариях. Можно запустить приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] из меню **Пуск** Windows 10, из меню **Сервис** в помощнике по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и из нескольких расположений в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
При первом запуске [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и выборе в меню **Файл** пункта **Создать трассировку** приложение отображает диалоговое окно **Соединение с сервером**, где можно указать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для подключения.  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Запуск приложения SQL Server Profiler из меню "Пуск" Windows 10  
-  Щелкните значок " **Пуск** " Windows или нажмите клавишу Windows и начните ввод "SQL Server Profiler 17". Когда появится плитка **SQL Server Profiler 17** , щелкните ее.   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Запуск SQL Server Profiler в помощнике по настройке ядра СУБД  
-  В меню [!INCLUDE[ssDE](../../includes/ssde-md.md)] Сервис **помощника по настройке компонента** выберите **SQL Server Profiler**.  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>Запуск SQL Server Profiler в SQL Server Management Studio  
 Вы можете начать [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] с нескольких расположений [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в. При запуске приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] загружается контекст подключения, шаблон трассировки и выполняется фильтрация контекста точки запуска. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]запускает каждый сеанс SQL Server Profiler в своем собственном экземпляре, и профилировщик продолжит работу при завершении работы [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Запуск приложения SQL Server Profiler из меню «Инструменты»  
-  В меню среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Инструменты** выберите **SQL Server Profiler**.  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Запуск приложения SQL Server Profiler из редактора запросов  
- В редакторе запросов щелкните правой кнопкой мыши, а затем выберите пункт **Трассировка запроса в приложении SQL Server Profiler**.  

  > [!NOTE]  
  >  Контекстом соединения является редактор соединения, шаблон трассировки — TSQL_SP, а применяемый фильтр SPID = окно запроса SPID.  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Запуск приложения SQL Server Profiler из монитора активности  
- В мониторе активности щелкните панель **Процессы**, щелкните правой кнопкой процесс, который хотите профилировать, а затем выберите пункт **Трассировка процесса в приложении SQL Server Profiler**.  

    > [!NOTE]  
    >  Когда выбран процесс, контекстом соединения является соединение обозревателя объектов при открытии монитора активности. Шаблон трассировки — это шаблон по умолчанию в зависимости от типа сервера, а идентификатор SPID равен идентификатору SPID для выбранного процесса.  
    
## <a name="net-framework-security"></a>Безопасность .NET Framework  
- В режиме проверки подлинности Windows учетная запись пользователя, от имени которой запускается приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], должна иметь разрешение на подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
- Для выполнения трассировки в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]пользователь должен также иметь разрешение ALTER TRACE.  

## <a name="next-steps"></a>Следующие шаги  
 [Обзор SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Использование среды SQL Server Management Studio](https://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
