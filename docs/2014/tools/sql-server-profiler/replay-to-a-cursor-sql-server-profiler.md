---
title: Воспроизведение до курсора (приложение SQL Server Profiler) | Документы Microsoft
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
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 90dd5a922aa0f4363dc73bf88989daec05568944
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100119"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>воспроизвести до курсора (приложение SQL Server Profiler)
  В этом подразделе описывается воспроизведение файлов или таблиц трассировки, которые были приостановлены по достижении курсора при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Приостановка трассировок курсоров поддерживает отладку, так как существует возможность разбиения воспроизведения длинных скриптов трассировки на короткие сегменты, которые могут анализироваться по шагам.  
  
### <a name="to-replay-to-the-cursor"></a>Воспроизведение до курсора  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Открытие файла трассировки (приложение SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) или [Открытие таблицы трассировки (приложение SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](replay-requirements.md).  
  
2.  В окне трассировки выберите событие.  
  
3.  В меню **Воспроизведение** выберите пункт **Выполнить до курсора**и подключитесь к серверу, на котором хотите воспроизвести трассировку.  
  
4.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**.  
  
     Воспроизведение начинается, останавливаясь по достижении первого курсора.  
  
5.  Для продолжения трассировки нажмите клавишу F5.  
  
6.  Повторяйте шаг 5 до завершения трассировки.  
  
## <a name="see-also"></a>См. также  
 [Воспроизведение до точки останова &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md)   
 [Воспроизведение трассировок](replay-traces.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  