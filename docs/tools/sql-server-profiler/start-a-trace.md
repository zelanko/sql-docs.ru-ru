---
title: Запуск трассировки
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: b7e2432d728b487fe0ea55a1e03c84f613c270d1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307808"
---
# <a name="start-a-trace"></a>Запуск трассировки

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

После определения новой трассировки или создания шаблона при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно запускать, приостанавливать или останавливать сбор данных, используя новое определение трассировки или новый шаблон.  
  
## <a name="starting-a-trace"></a>Запуск трассировки

Когда запускается трассировка, а определенным источником является экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] или служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает очередь, служащую для временного хранения данных о зарегистрированных серверных событиях.  
  
При обращении к инструменту трассировки SQL посредством приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] открывается новое окно трассировки (если ни одно такое окно еще не открыто) и немедленно выполняется регистрация данных.  
  
Если обращение следует к механизму трассировки SQL с использованием системных хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] , трассировку нужно запускать каждый раз, когда экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинает регистрацию данных. После запуска трассировки можно изменить только ее имя.  
  
> [!NOTE]  
>  При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку.  
  
## <a name="see-also"></a>См. также:

[Автоматический запуск трассировки после соединения с сервером (приложение SQL Server Profiler)](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   

[Приостановка трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   

[Остановка трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   

[Очистка окна трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   

[Проведение трассировки после паузы или остановки (SQL Server Profiler)](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)