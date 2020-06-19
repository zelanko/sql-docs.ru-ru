---
title: Воспроизвести до курсора (SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1bfba95925d041c61939947efe7d8f4432cba42
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007406"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>воспроизвести до курсора (приложение SQL Server Profiler)
  В этом подразделе описывается воспроизведение файлов или таблиц трассировки, которые были приостановлены по достижении курсора при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Приостановка трассировок курсоров поддерживает отладку, так как существует возможность разбиения воспроизведения длинных скриптов трассировки на короткие сегменты, которые могут анализироваться по шагам.  
  
### <a name="to-replay-to-the-cursor"></a>Воспроизведение до курсора  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](replay-requirements.md).  
  
2.  В окне трассировки выберите событие.  
  
3.  В меню **Воспроизведение** выберите пункт **Выполнить до курсора**и подключитесь к серверу, на котором хотите воспроизвести трассировку.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
     Воспроизведение начинается, останавливаясь по достижении первого курсора.  
  
5.  Для продолжения трассировки нажмите клавишу F5.  
  
6.  Повторяйте шаг 5 до завершения трассировки.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение нагрузки до точки останова (приложение SQL Server Profiler)](replay-to-a-breakpoint-sql-server-profiler.md)   
 [Воспроизведение трассировок](replay-traces.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
