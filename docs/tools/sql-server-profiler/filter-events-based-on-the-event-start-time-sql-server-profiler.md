---
title: "Фильтрация событий по времени начала события (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8c44076c02f6ecc2182927e4b46749424255a03d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>фильтровать события по времени начала (приложение SQL Server Profiler)
  В этом разделе описана фильтрация событий трассировки по времени начала с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>Фильтрация событий по времени начала события  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке имен **Использовать шаблон**выберите шаблон трассировки.  
  
4.  При необходимости задайте целевые расположения для сохранения результатов трассировки.  
  
5.  На вкладке **Выбор событий**щелкните заголовок столбца **StartTime** . Кроме того, для открытия диалогового окна **Редактирование фильтра** щелкните правой кнопкой мыши заголовок столбца и выберите пункт **Изменить фильтр** .  
  
6.  Раскройте **Больше** или **Меньше**и введите значение **datetime** в поле, которое появится под оператором сравнения.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

