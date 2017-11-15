---
title: "Категория событий Locks | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8887c507a61246c7ec12a6974402fe3576e9d1d4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="locks-event-category"></a>Категория событий Locks
  Классы событий в категории **Блокировки** применяются для контроля за активностью блокировок в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Эти классы событий помогают исследовать связанные с блокировками проблемы, вызванные одновременным чтением и записью данных несколькими пользователями.  
  
 Поскольку компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] часто обрабатывает большое количество блокировок, перехват событий из категории **Блокировки** во время трассировки может существенно увеличить нагрузку и размер файлов и таблиц трассировки.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Deadlock Graph](../../relational-databases/event-classes/deadlock-graph-event-class.md)|Предоставляет описание взаимоблокировки в формате XML.|  
|[Класс событий Lock:Acquired](../../relational-databases/event-classes/lock-acquired-event-class.md)|Указывает, что была получена блокировка ресурса, например строки в таблице.|  
|[Класс событий Lock:Cancel](../../relational-databases/event-classes/lock-cancel-event-class.md)|Отслеживает запросы на получение блокировки, которые были отменены до ее получения (например, чтобы избежать взаимоблокировки).|  
|[Класс событий Lock:Deadlock Chain](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)|Отслеживает возникновение условий взаимоблокировки и объектов, которые в них участвуют.|  
|[Класс событий Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)|Отслеживает момент, когда транзакция запрашивает блокировку на ресурс, уже блокированный другой транзакцией, в результате чего происходит взаимоблокировка.|  
|[Класс событий Lock:Escalation](../../relational-databases/event-classes/lock-escalation-event-class.md)|Указывает, что мелкогранулированная блокировка была преобразована в крупногранулированную.|  
|[Класс событий Lock:Released](../../relational-databases/event-classes/lock-released-event-class.md)|Отслеживает освобождение блокировки.|  
|[Класс событий Lock:Timeout (timeout &#62; 0)](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)|Отслеживает запросы блокировок, которые не удалось выполнить, поскольку запрошенный ресурс был блокирован другой транзакцией. Это событие происходит только тогда, когда время ожидания блокировки больше нуля.|  
|[Класс событий Lock:Timeout](../../relational-databases/event-classes/lock-timeout-event-class.md)|Отслеживает запросы блокировок, которые не удалось выполнить, поскольку запрошенный ресурс был блокирован другой транзакцией.|  
  
  
