---
title: Определение частоты опроса - Analytics Platform System | Документация Майкрософт
description: В этой статье объясняется, как определить частоту опроса для Analytics Platform System appliance оповещений.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2d305c766801ce27268e2d3bc873d9c361c034f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961075"
---
# <a name="determine-polling-frequency"></a>Определение частоты опроса
В этой статье объясняется, как определить частоту опроса для Analytics Platform System appliance оповещений.  
  
## <a name="to-determine-the-polling-frequency"></a>Для определения частоты опроса  
Поскольку PDW не поддерживает необходимые уведомления при возникновении оповещений, решение для мониторинга необходимо постоянно опрашивать устройство библиотеки DLL.  На внутреннем уровне PDW опрашивает компоненты с разными интервалами:  
  
-   Кластер — 60 секунд  
  
-   Периодический сигнал - 60 секунд  
  
-   Все другие компоненты — пять минут  
  
-   Счетчики производительности — три секунды  
  
Распространенные интервал опроса для оповещений, который также используется в System Center, — **каждые 15 минут**.  Очевидно, что вам удалось запросить более или менее часто, но не рекомендуется для опроса меньше, чем каждые шесть часов.  
  
Увеличением частоты опросов приемлема, но слишком часто опроса может перегрузить [sys.dm_pdw_nodes_exec_requests](https://msdn.microsoft.com/library/ms177648(v=sql11).aspx) динамического административного Представления.  Слишком часто опроса может сделать его сложно для пользователей, для диагностики производительности запросов проблем при их быстро возвращает из представления.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройства &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
