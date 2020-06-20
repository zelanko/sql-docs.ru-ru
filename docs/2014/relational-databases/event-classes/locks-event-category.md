---
title: Категория событий Locks | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a202279021e3e6c7c3c44a167792bb9439567aa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85029292"
---
# <a name="locks-event-category"></a>Категория событий Locks
  Классы событий в категории **Locks** применяются для контроля за активностью блокировок в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Эти классы событий помогают исследовать связанные с блокировками проблемы, вызванные одновременным чтением и записью данных несколькими пользователями.  
  
 Поскольку компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] часто обрабатывает большое количество блокировок, перехват событий из категории **Блокировки** во время трассировки может существенно увеличить нагрузку и размер файлов и таблиц трассировки.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий Deadlock Graph](deadlock-graph-event-class.md)|Предоставляет описание взаимоблокировки в формате XML.|  
|[Класс событий Lock:Acquired](lock-acquired-event-class.md)|Указывает, что была получена блокировка ресурса, например строки в таблице.|  
|[Класс событий Lock:Cancel](lock-cancel-event-class.md)|Отслеживает запросы на получение блокировки, которые были отменены до ее получения (например, чтобы избежать взаимоблокировки).|  
|[Класс событий Lock:Deadlock Chain](lock-deadlock-chain-event-class.md)|Отслеживает возникновение условий взаимоблокировки и объектов, которые в них участвуют.|  
|[Класс событий Lock:Deadlock](lock-deadlock-event-class.md)|Отслеживает момент, когда транзакция запрашивает блокировку на ресурс, уже блокированный другой транзакцией, в результате чего происходит взаимоблокировка.|  
|[Класс событий Lock:Escalation](lock-escalation-event-class.md)|Указывает, что мелкогранулированная блокировка была преобразована в крупногранулированную.|  
|[Класс событий Lock:Released](lock-released-event-class.md)|Отслеживает освобождение блокировки.|  
|[Класс событий Lock:Timeout (timeout &#62; 0)](lock-timeout-timeout-0-event-class.md)|Отслеживает запросы блокировок, которые не удалось выполнить, поскольку запрошенный ресурс был блокирован другой транзакцией. Это событие происходит только тогда, когда время ожидания блокировки больше нуля.|  
|[Класс событий Lock:Timeout](lock-timeout-event-class.md)|Отслеживает запросы блокировок, которые не удалось выполнить, поскольку запрошенный ресурс был блокирован другой транзакцией.|  
  
  
