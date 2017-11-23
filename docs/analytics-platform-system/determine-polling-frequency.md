---
title: "Определить частоту опроса (система платформы аналитики)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062c0e3d-f7d0-44f1-aeab-a9bd17dc6fdd
caps.latest.revision: "7"
ms.openlocfilehash: fb32abc38a90cd7450dc310a9f73eb7a5d72b5fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="determine-polling-frequency"></a>Определение частоты опроса
В этом разделе объясняется, как определить частоту опроса для SQL Server PDW appliance оповещений.  
  
## <a name="to-determine-the-polling-frequency"></a>Для определения частоты опроса  
Поскольку PDW сейчас не поддерживает упреждающее уведомления при возникновении оповещений, решение для мониторинга необходимо постоянно опрашивать устройство библиотеки DLL.  На внутреннем уровне PDW опрашивает компоненты различные интервалы:  
  
-   Кластер — 60 секунд  
  
-   Пульс — 60 секунд  
  
-   Все другие компоненты — 5 минут  
  
-   Счетчики производительности — 3 секунды  
  
— Общий интервал опроса для оповещений, который также используется в System Center, **каждые 15 минут**.  Очевидно может запросить более или менее часто, но не рекомендуется для опроса меньше, чем каждые 6 часов.  
  
Опрос чаще приемлема, но опрос слишком часто может загромождать [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/en-us/library/ms177648(v=sql11).aspx) динамического административного Представления.  Это может усложнить для пользователей, для диагностики проблем с производительностью запросов, если существует быстрее запросов выполняет накат скрывается.  
  
## <a name="see-also"></a>См. также:  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройства &#40; Система платформы аналитики &#41;](appliance-monitoring.md)  
  
