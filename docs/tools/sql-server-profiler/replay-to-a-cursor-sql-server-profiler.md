---
title: "Воспроизведение до курсора (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 775216d4634aced69ecc3248064b9539599fe54c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>воспроизвести до курсора (приложение SQL Server Profiler)
  В этом подразделе описывается воспроизведение файлов или таблиц трассировки, которые были приостановлены по достижении курсора при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Приостановка трассировок курсоров поддерживает отладку, так как существует возможность разбиения воспроизведения длинных скриптов трассировки на короткие сегменты, которые могут анализироваться по шагам.  
  
### <a name="to-replay-to-the-cursor"></a>Воспроизведение до курсора  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в разделах [Открытие файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или [Открытие таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  В окне трассировки выберите событие.  
  
3.  В меню **Воспроизведение** выберите пункт **Выполнить до курсора**и подключитесь к серверу, на котором хотите воспроизвести трассировку.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
     Воспроизведение начинается, останавливаясь по достижении первого курсора.  
  
5.  Для продолжения трассировки нажмите клавишу F5.  
  
6.  Повторяйте шаг 5 до завершения трассировки.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение до точки останова &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

