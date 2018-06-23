---
title: Фильтрация событий по времени окончания (приложение SQL Server Profiler) | Документы Майкрософт
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
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6ba13adfd2cd482a8c52383ae220557f0bcc66
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191112"
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
  
6.  Разверните **больше** или **меньше, чем**и введите `datetime`значение в поле, находящееся под оператором сравнения.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  