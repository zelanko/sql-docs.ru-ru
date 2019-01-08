---
title: Сопоставление трассировки с журналом производительности Windows | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
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
ms.openlocfilehash: 3c8a3d7a9888423d312d578784e1f7e1ff75434d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754806"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>Сопоставление трассировки с журналом производительности Windows
  С помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]можно открыть журнал производительности Microsoft Windows, выбрать счетчики, которые нужно сопоставить с трассировкой, и отобразить выбранные счетчики производительности рядом с трассировкой в графическом пользовательском интерфейсе приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . При выборе события в окне трассировки вертикальная красная линия на панели окна системного монитора в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] показывает данные журнала производительности, которые сопоставлены выбранному событию трассировки.  
  
 Чтобы сопоставить трассировку со счетчиками производительности, откройте файл трассировки или таблицу, содержащую столбцы данных **Начальное время** и **Конечное время** data columns, и then click **Импортировать данные производительности** в меню приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Файл** . Потом можно открыть журнал производительности и выбрать объекты системного монитора и счетчики, которые сопоставляются с трассировкой.  
  
## <a name="see-also"></a>См. также  
 [Сопоставление трассировки с журналом производительности Windows (приложение SQL Server Profiler)](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
