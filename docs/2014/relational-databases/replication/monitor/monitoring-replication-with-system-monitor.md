---
title: Наблюдение за репликацией с помощью системного монитора | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], System Monitor
- System Monitor [SQL Server], replication
- performance counters [SQL Server replication]
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b5d1a63937a11da4703ec4ef0338dee89a5c33f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62667309"
---
# <a name="monitoring-replication-with-system-monitor"></a>Наблюдение за репликацией с помощью системного монитора
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]Системный монитор Windows позволяет использовать графики, диаграммы и отчеты для оценки эффективности компьютера, а также выявлять и устранять возможные проблемы (например, несбалансированное использование ресурсов, нехватка оборудования или неплохая разработка программ) и планировать Дополнительные требования к оборудованию. Дополнительные сведения см. в статье [Наблюдение за использованием ресурсов (системный монитор)](../../performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 Системный монитор использует объекты и счетчики производительности, предоставляющие информацию о производительности различных процессов. Производительность репликации можно оценить с помощью счетчиков, связанных с агентами репликации:  
  
|Агент|Объект производительности|Счетчик|Description|  
|-----------|------------------------|-------------|-----------------|  
|Все агенты|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: агенты репликации|Запущен|Число агентов репликации, запущенных в данный момент времени.|  
|агент моментальных снимков|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: моментальный снимок репликации|Snapshot: Delivered Cmds/sec|Число команд, доставленных распространителю в секунду.|  
|агент моментальных снимков|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: моментальный снимок репликации|Моментальный снимок: доставлено транзакций/с|Количество транзакций, доставленных распространителю за секунду.|  
|Агент чтения журнала.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: средство чтения журнала репликации|Logreader: Delivered Cmds/sec|Число команд, доставленных распространителю в секунду.|  
|Агент чтения журнала.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: средство чтения журнала репликации|Logreader: Delivered Trans/sec|Количество транзакций, доставленных распространителю за секунду.|  
|Агент чтения журнала.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: средство чтения журнала репликации|Logreader: Delivery Latency|Текущее количество времени, в миллисекундах, прошедшего с момента применения транзакций на издателе до момента доставки транзакций распространителю.|  
|Агент распространителя|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: распространитель репликации.|Dist: Delivered Cmds/sec|Количество команд, доставленных подписчику за секунду.|  
|Агент распространителя|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: распространитель репликации.|Dist: Delivered Trans/sec|Количество транзакций, доставленных подписчику за секунду.|  
|Агент распространителя|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: распространитель репликации.|Dist: Delivery Latency|Текущее количество времени, в миллисекундах, прошедшего с момента доставки транзакций распространителю до момента применения транзакций у подписчика.|  
|Агент слияния.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: слияние репликации|Конфликтов/сек|Число конфликтов в секунду во время процесса слияния.|  
|Агент слияния.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: слияние репликации|Загружено изменений/сек|Число строк в секунду, реплицированных с издателя на подписчик.|  
|Агент слияния.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: слияние репликации|Выгружено изменений/сек|Число строк в секунду, реплицируемых с подписчика на издатель.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией &#40;&#41;](../monitoring-replication.md)  
  
  
