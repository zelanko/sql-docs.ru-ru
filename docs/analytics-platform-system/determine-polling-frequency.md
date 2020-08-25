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
ms.openlocfilehash: cafd18a7701ed5de5018a3e8dc23bc8d5d9640fa
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767043"
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
  
Чаще всего опрос является приемлемым, но слишком часто опрос может перегружать динамическое административное представление [sys. dm_pdw_nodes_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md?view=sql-server-ver15) .  Слишком частое выполнение опроса может затруднять пользователям диагностировать проблемы с производительностью запросов, когда они быстро выходят из представления.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройств &#40;системная платформа аналитики&#41;](appliance-monitoring.md)  
