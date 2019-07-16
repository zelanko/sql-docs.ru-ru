---
title: Мониторинг устройства - Analytics Platform System | Документация Майкрософт
description: В этом руководстве мониторинга устройство описывает средства и задачи, для мониторинга Analytics Platform System appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cb25a5eccd1e77f08cedc74ad8042e0dc573605c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961500"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Мониторинг устройства для Analytics Platform System
В этом руководстве мониторинга устройство описывает средства и задачи, для мониторинга Analytics Platform System appliance.  
  
## <a name="Basics"></a>Основы мониторинга и средства  
Значения и сведения, которые можно отслеживать на SQL Server PDW appliance доступны широкие. Например ниже приведены типичные задачи по мониторингу.  
  
-   Проверьте наличие любого оповещения, выданный службой SQL Server PDW.  
  
-   Наблюдение за сбоя оборудования.  
  
-   Наблюдение за проблемы с сетевым подключением.  
  
-   Проверьте наличие ошибок, возвращаемых во время обработки запросов.  
  
-   Просмотрите число текущих активных сеансов и запросов.  
  
-   Проверьте состояние загрузки, резервного копирования и восстановления.  
  
### <a name="appliance-monitoring-tools"></a>Устройства, средства мониторинга  
Существует несколько средств, доступных для мониторинга устройства.  
  
Консоль администрирования  
SQL Server PDW имеет на консоль администратора. Это веб-средство, отображающее сведения о запросах, загрузки, резервного копирования и восстановления, блокировки, сеансы, оповещения и состояние устройства. Консоль администратора выполняется на устройстве; пользователи подключаться к консоли администрирования через Internet Explorer. Дополнительные сведения см. в разделе:  
  
-   [Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![Предупреждения консоли администрирования PDW](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Системные представления  
SQL Server PDW включает в себя комплексное системных представлений, которые позволяют получить подробные сведения о работоспособности устройства, состояние и производительность. Список системных представлений для отслеживания задач см. в разделе:  
  
-   [Мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW имеет расширенную интеграцию с помощью Systems Center Operations Manager. Пакеты управления для SQL Server PDW доступны для бесплатной загрузки. Дополнительные сведения об использовании System Center для наблюдения за SQL Server PDW см. в следующих:  
  
-   [Мониторинг устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Пользовательские решения  
Для ситуаций, System Center недоступна в вашем центре обработки данных, средства отслеживания, можно наблюдать за устройства с помощью стороннего решения для мониторинга. Установка агентов внешнего программного обеспечения в настоящее время не поддерживается в PDW, но большинство решений мониторинга поддерживает Transact\-интеграции SQL, чтобы системный администратор может реализовать прямой Transact\-SQL-запросов к PDW устройство.  
  
Если решение мониторинга не поддерживает прямое Transact\-SQL-запросы, или не иметь средство наблюдения, а затем скрипты можно использовать для выполнения задач наблюдения, например, отправку по электронной почте при появлении предупреждения.  Вики-сайте TechNet пример сценария мониторинга решения.  
  
-   [Power Shell примера мониторинга для SQL Server PDW](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Связанные задачи по мониторингу  
  
|Задача мониторинга|Описание|  
|-------------------|---------------|  
|Мониторинг устройства с помощью консоли администрирования.|[Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Мониторинг устройства с помощью системных представлений.|[Мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Мониторинг устройства с помощью System Center|[Мониторинг устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Отслеживайте состояние устройства.|[Состояние работоспособности монитора устройство &#40;Analytics Platform System&#41;](monitor-appliance-health-state.md)|  
|Мониторинг пакетов пульса.|[Отправка отзыва о телеметрии в корпорацию Майкрософт &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Отслеживание оповещений устройства.|[Отслеживание оповещений устройства &#40;Analytics Platform System&#41;](track-appliance-alerts.md)|  
|Определите, какой объем ресурсов, используется.|[Просмотреть сведения об использовании емкости &#40;Analytics Platform System&#41;](view-capacity-utilization.md)|  
|Определите, как часто будут опрашивать устройство.|[Определение частоты опроса &#40;Analytics Platform System&#41;](determine-polling-frequency.md)|  
|При возникновении сбоя кластера, определить, какому кластеру неисправного узла.|[Определите, какой узел кластера не удалось &#40;Analytics Platform System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Задачи управления устройствами &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
