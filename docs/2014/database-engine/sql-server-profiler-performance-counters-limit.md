---
title: SQL Server Profiler — ограничение счетчиков производительности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27bda135abaf9d91b078e36a69a87098a734acbc
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928568"
---
# <a name="sql-server-profiler---performance-counters-limit"></a>Приложение SQL Server Profiler — предел для счетчиков производительности
  Используйте диалоговое окно «Предел для счетчиков производительности», чтобы ограничить сведения из файла журнала производительности системного монитора при сопоставлении ее с трассировкой приложения [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] . Можно использовать это диалоговое окно, чтобы выбрать счетчики, которые следует отобразить и использовать для сопоставления.  
  
 Диалоговое окно **Предел для счетчиков производительности** заполняется объектами производительности и счетчиками, которые содержатся в файле журнала производительности.  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a>Выбор объектов производительности и счетчиков для сопоставления с трассировкой  
  
1.  Разверните объект производительности, чтобы увидеть, какие счетчики включены в файл журнала производительности.  
  
2.  Установите флажки рядом со счетчиками, которые необходимо сопоставить с файлом трассировки приложения [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] .  
  
     Если нужно выбрать все счетчики объекта производительности, установите пометку на флажке рядом с объектом производительности. Пометив самый верхний узел, обозначающий компьютер, можно выбрать все объекты производительности и счетчики, содержащиеся в файле журнала производительности.  
  
## <a name="see-also"></a>См. также:  
 [Сопоставить трассировку с данными журнала производительности Windows (приложение SQL Server Profiler)](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
