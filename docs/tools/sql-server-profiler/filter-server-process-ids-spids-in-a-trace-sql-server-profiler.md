---
title: "Отфильтровать идентификаторы процессов сервера (SPID) в трассировке (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a41b9ade1c1336d8e2591e136054f6fd81c57eea
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>отфильтровать идентификаторы процессов сервера (SPID) в трассировке (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Описывается, как отфильтровать идентификаторы процессов сервера (SPID) в трассировке при использовании приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Фильтрация системных идентификаторов в трассировке  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру SQL Server.  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке имен **Использовать шаблон**выберите шаблон трассировки.  
  
4.  Можно также задать целевой файл или таблицу, в которых будут сохраняться результаты трассировки.  
  
5.  На вкладке **Выбор событий**щелкните заголовок столбца **SPID**, чтобы открыть диалоговое окно **Изменение фильтра** . Можно также правой кнопкой мыши щелкнуть заголовок столбца и выбрать пункт **Изменить фильтр столбца**. Если столбец **SPID** не отображается, установите флажок **Показать все столбцы** .  
  
6.  В диалоговом окне **Изменение фильтра** раскройте соответствующий оператор сравнения и введите SPID как значение для сравнения.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
