---
title: Определить частоту опроса - система платформы аналитики | Документы Microsoft
description: В этой статье объясняется, как определить частоту опроса для оповещения устройства Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e8e2a1ccf469e6c587870c0d5921014d797f87d1
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="determine-polling-frequency"></a>Определение частоты опроса
В этой статье объясняется, как определить частоту опроса для оповещения устройства Analytics Platform System.  
  
## <a name="to-determine-the-polling-frequency"></a>Для определения частоты опроса  
Поскольку PDW сейчас не поддерживает упреждающее уведомления при возникновении оповещений, решение для мониторинга необходимо постоянно опрашивать устройство библиотеки DLL.  На внутреннем уровне PDW опрашивает компоненты различные интервалы:  
  
-   Кластер — 60 секунд  
  
-   Пульс — 60 секунд  
  
-   Все другие компоненты — пять минут  
  
-   Счетчики производительности — три секунды  
  
— Общий интервал опроса для оповещений, который также используется в System Center, **каждые 15 минут**.  Очевидно может запросить более или менее часто, но не рекомендуется для опроса меньше, чем каждые шесть часов.  
  
Опрос чаще приемлема, но опрос слишком часто может загромождать [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/en-us/library/ms177648(v=sql11).aspx) динамического административного Представления.  Слишком часто опроса может сделать его сложно для пользователей, для диагностики производительности запросов проблемы при их быстрее выполняет накат скрывается.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройства &#40;система платформы аналитики&#41;](appliance-monitoring.md)  
  
