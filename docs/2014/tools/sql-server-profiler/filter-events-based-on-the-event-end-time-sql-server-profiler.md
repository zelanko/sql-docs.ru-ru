---
title: Фильтрация событий по времени окончания (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23c9ca00077d64fe72f775d343640a15dfc38f50
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194384"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>фильтровать события на основе времени окончания события (приложение SQL Server Profiler)
  В этом подразделе описывается, как при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]отфильтровать события трассировки на основе времени окончания события.  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>Фильтрование событий на основе времени окончания события  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В диалоговом окне **Свойства трассировки** выберите вкладку **Общие** и введите имя в текстовое поле **Имя трассировки** .  
  
3.  В списке **Использовать шаблон**выберите шаблон трассировки.  
  
4.  Можно также задать целевой файл или таблицу, в которых будут сохраняться результаты трассировки.  
  
5.  На вкладке **Выбор событий**щелкните столбец данных **EndTime** , чтобы открыть диалоговое окно **Изменение фильтра** . Можно также щелкнуть правой кнопкой мыши заголовок столбца и выбрать пункт **Изменить фильтр столбца**.  
  
6.  Разверните **больше, чем** или **меньше, чем**и введите `datetime`значение в поле, находящееся под оператором сравнения.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
