---
title: "Воспроизведение до точки останова (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3aabc8e1ed9ac28f8b998c20f815a207ed891009
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>воспроизвести нагрузку до точки останова (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В этом разделе описывается задание точек останова в файл трассировки или таблицы, который требуется воспроизвести с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Определение точек останова перед запуском воспроизведения трассировки позволяет останавливать ее по определенным событиям. Точки останова позволяют отлаживать воспроизведение трассировки, разбивая длинный скрипт трассировки на короткие сегменты, которые могут быть подвергнуты последовательному анализу.  
  
### <a name="to-replay-to-a-breakpoint"></a>Воспроизведение до точки останова  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в разделах [Открытие файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или [Открытие таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  В окне трассировки щелкните событие, по которому устанавливается точка останова. Точку останова можно назначить одним из следующих трех способов:  
  
    -   Нажмите клавишу F9.  
  
    -   В меню **Воспроизведение** выбрав пункт **Переключить точку останова**.  
  
    -   Щелкнув событие правой кнопкой мыши, а затем выбрав пункт **Переключить точку останова**.  
  
     Справа от выбранного события трассировки появляется красный маркер, указывающий на наличие точки останова.  
  
     Повторите этот шаг для установки нескольких точек останова.  
  
3.  В меню **Воспроизведение** выберите **Начать**и подключитесь к серверу, на котором будет воспроизводиться трассировка.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
     Воспроизведение начинается, приостанавливаясь при достижении точки останова.  
  
5.  Нажмите F5 для возобновления воспроизведения до следующей точки останова.  
  
6.  Повторяйте шаг 5 до завершения трассировки.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизвести нагрузку до курсора (приложение SQL Server Profiler)](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)   
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
