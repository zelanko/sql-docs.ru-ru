---
title: Сопоставление трассировки с журналом производительности Windows | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d8806911251c15a8de0e7f71f032038c8686df4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217844"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>Сопоставление трассировки с журналом производительности Windows
  С помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно открыть журнал производительности Microsoft Windows, выбрать счетчики, которые нужно сопоставить с трассировкой, и отобразить выбранные счетчики производительности рядом с трассировкой в графическом пользовательском интерфейсе приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . При выборе события в окне трассировки вертикальная красная линия на панели окна системного монитора в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] показывает данные журнала производительности, которые сопоставлены выбранному событию трассировки.  
  
 Чтобы сопоставить трассировку со счетчиками производительности, откройте файл трассировки или таблицу, содержащую столбцы данных **Начальное время** и **Конечное время** data columns, и then click **Импортировать данные производительности** в меню приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Файл** . Потом можно открыть журнал производительности и выбрать объекты системного монитора и счетчики, которые сопоставляются с трассировкой.  
  
## <a name="see-also"></a>См. также  
 [Сопоставить трассировку с данными журнала производительности Windows (приложение SQL Server Profiler)](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
