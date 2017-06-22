---
title: "Улучшение доступа к данным трассировки | Документация Майкрософт"
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
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c20ce109f48cf8791ddb3116258c52b0d3ba70e8
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="improve-access-to-trace-data"></a>Улучшение доступа для трассировки данных
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] использует пространство в каталоге **temp** для улучшения доступа к трассировке данных. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] требует по крайней мере 10 мегабайт (МБ) свободного пространства. Если во время работы приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]объем свободного места становится менее 10 Мб, то выполнение всех функций [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] прекращается.  
  
 Использование приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] места в каталоге **temp** может вызвать быстрое увеличение объема каталога **temp** . Чтобы избежать проблем с увеличением объема файлов, можно поместить каталог **temp** на диск, не являющийся системным; для этого необходимо изменить значение переменной среды TEMP.  
  
 В следующей процедуре описаны действия, необходимые для изменения значения переменной среды TEMP в большинстве операционных систем Microsoft Windows. Дополнительные сведения об установке значений переменных среды см. в документации по операционной системе Windows.  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a>Изменение значения переменной среды TEMP в операционных системах Windows  
  
1.  В меню **Пуск** выберите пункт **Панель управления**, а затем выберите **Система**.  
  
2.  В диалоговом окне **Свойства системы** выберите вкладку **Дополнительно** , затем нажмите кнопку **Переменные среды**.  
  
3.  Прокрутите вниз список **Системные переменные**, выберите строку, соответствующую переменной **TEMP** , затем нажмите **Изменить**.  
  
4.  В диалоговом окне **Изменение системной переменной** введите путь и имя диска и каталога, где необходимо разместить каталог **temp** .  
  
5.  Нажмите **ОК** для сохранения изменений.  
  
## <a name="see-also"></a>См. также:  
 [Запуск приложения SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
