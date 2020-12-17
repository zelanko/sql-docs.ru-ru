---
title: Определение частоты опроса
description: В этой статье объясняется, как определить частоту опроса для оповещений устройства аналитики системы.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee5c83fee1028b7e165db6dfb8015129c29e4eca
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97641481"
---
# <a name="determine-polling-frequency"></a>Определение частоты опроса
В этой статье объясняется, как определить частоту опроса для оповещений устройства аналитики системы.  
  
## <a name="to-determine-the-polling-frequency"></a>Определение частоты опроса  
Так как PDW в настоящее время не поддерживает упреждающие уведомления при возникновении предупреждений, решение для мониторинга должно постоянно опрашивать библиотеки DLL устройства.  На внутреннем этапе PDW опрашивает компоненты с разными интервалами:  
  
-   Кластер — 60 секунд  
  
-   Пульс — 60 секунд  
  
-   Все остальные компоненты — пять минут  
  
-   Счетчики производительности — три секунды  
  
Общий интервал опроса оповещений, который также используется System Center, составляет **каждые 15 минут**.  Очевидно, что вы можете запросить больше или реже, но не рекомендуется выполнять опрос менее чем за шесть часов.  
  
Чаще всего опрос является приемлемым, но слишком часто опрос может перегружать [sys.dm_pdw_nodes_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) DMV.  Слишком частое выполнение опроса может затруднять пользователям диагностировать проблемы с производительностью запросов, когда они быстро выходят из представления.  
  
## <a name="see-also"></a>См. также:  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройств &#40;системная платформа аналитики&#41;](appliance-monitoring.md)  
