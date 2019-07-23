---
title: Улучшение доступа к данным трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a94926a2876c5cac52560872dc9fc59e50ba6ad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072883"
---
# <a name="improve-access-to-trace-data"></a>Улучшение доступа для трассировки данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
