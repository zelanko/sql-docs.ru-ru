---
title: Свойства (вкладка «Выбор событий») трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d86ae88fba4cb817ea7966daa60932238c7f0460
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842433"
---
# <a name="trace-properties-events-selection-tab"></a>Свойства трассировки (вкладка «Выбор событий»)
  Вкладка **Выбор событий** диалогового окна **Свойства трассировки** используется для просмотра и указания трассируемых событий и столбцов данных.  
  
## <a name="options"></a>Параметры  
 Столбец**События**   
 Укажите трассируемые события, устанавливая или снимая флажок в соответствующем столбце. **События** упорядочены по категориям событий. Классы событий, указанные в шаблоне, выбираются автоматически. Дополнительные сведения см. в разделе [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Столбцы данных  
 Укажите трассируемые столбцы данных, устанавливая флажки для соответствующих событий и столбцов данных. Для каждого из событий, включенных в трассировку, все основные столбцы отмечены по умолчанию.  
  
 Для определения фильтра щелкните заголовок столбца данных и введите критерии фильтра. Отфильтрованные столбцы данных отображаются значком фильтра слева от метки столбца в диалоговом окне **Изменение фильтра** . Дополнительные сведения см. в разделе [SQL Server Profiler - Edit Filter](../../2014/database-engine/sql-server-profiler-edit-filter.md).  
  
 **Показать все события**  
 Показать все доступные события. По умолчанию отображаются только те строки, которые отмечены в сетке **Выбор событий** . Снимите этот флажок, чтобы скрыть все события, не выбранные в сетке **Выбор событий** .  
  
 **Показать все столбцы**  
 Показать все доступные столбцы данных. По умолчанию отображаются только выбранные столбцы данных. Снимите этот флажок, чтобы скрыть все невыбранные столбцы данных в сетке **Выбор событий** .  
  
 **Фильтры столбцов**  
 Открывает диалоговое окно **Изменение фильтра** . Это диалоговое окно предназначено для редактирования фильтров столбцов данных.  
  
 **Систематизировать столбцы**  
 Изменяет порядок следования столбцов в трассировке и группирует результаты по одному или нескольким столбцам.  
  
## <a name="see-also"></a>См. также  
 [Указание столбцов событий и данных для файла трассировки (приложение SQL Server Profiler)](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Упорядочивание столбцов, отображаемых в трассировке &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Фильтрация событий в трассировке &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Просмотр сведений фильтров (приложение SQL Server Profiler)](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Изменение фильтра &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
