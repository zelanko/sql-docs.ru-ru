---
title: Запуск трассировки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb735810bcf265076fde9e3834dc7404d1f45079
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188365"
---
# <a name="start-a-trace"></a>Запуск трассировки
  После определения новой трассировки или создания шаблона при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно запускать, приостанавливать или останавливать сбор данных, используя новое определение трассировки или новый шаблон.  
  
## <a name="starting-a-trace"></a>Запуск трассировки  
 Когда запускается трассировка, а определенным источником является экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] или служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает очередь, служащую для временного хранения данных о зарегистрированных серверных событиях.  
  
 При обращении к инструменту трассировки SQL посредством приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] открывается новое окно трассировки (если ни одно такое окно еще не открыто) и немедленно выполняется регистрация данных.  
  
 Если обращение следует к механизму трассировки SQL с использованием системных хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] , трассировку нужно запускать каждый раз, когда экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинает регистрацию данных. После запуска трассировки можно изменить только ее имя.  
  
> [!NOTE]  
>  При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку.  
  
## <a name="see-also"></a>См. также  
 [Запуск трассировки после соединения с сервером, автоматически &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Приостановка трассировки (приложение SQL Server Profiler)](pause-a-trace-sql-server-profiler.md)   
 [Остановка трассировки (приложение SQL Server Profiler)](stop-a-trace-sql-server-profiler.md)   
 [Очистка окна трассировки (приложение SQL Server Profiler)](clear-a-trace-window-sql-server-profiler.md)   
 [Проведение трассировки после паузы или остановки (SQL Server Profiler)](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  