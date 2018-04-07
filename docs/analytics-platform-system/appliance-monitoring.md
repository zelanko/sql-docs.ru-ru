---
title: Устройство мониторинга (система платформы аналитики)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 253864fb-9178-41d2-a0ae-5dd9fd0a4fda
caps.latest.revision: 25
ms.openlocfilehash: f361b56581fd5a8dadb4ff41c387074abc006879
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="appliance-monitoring"></a>Мониторинг устройства
Это руководство по устройства наблюдения описываются средства и задачи для мониторинга SQL Server PDW appliance.  
  
## <a name="Basics"></a>Основы и средств мониторинга  
Значения и сведения, которые можно отслеживать в SQL Server PDW appliance — это широко. Например ниже приведены типичные задачи наблюдения.  
  
-   Проверьте все предупреждения, выданные SQL Server PDW.  
  
-   Наблюдение за сбоя оборудования.  
  
-   Наблюдение за проблем с сетевым подключением.  
  
-   Проверьте наличие ошибок, возвращаемых для пользователей во время обработки запроса.  
  
-   Просмотр количества активных сеансов и запросов.  
  
-   Проверьте состояние загрузки, резервное копирование и восстановление.  
  
### <a name="appliance-monitoring-tools"></a>Устройства, средства мониторинга  
Существует несколько средств, доступных для устройства наблюдения.  
  
Административная консоль  
SQL Server PDW имеет на консоль администратора. Это веб-средство, которое отображает сведения о запросах, загрузки, резервного копирования и восстановления, блокировки, сеансы, предупреждения и состояние устройства. Консоль администратора выполняется на устройстве; пользователи подключаться к консоли администрирования через Internet Explorer. Дополнительные сведения см. в разделе:  
  
-   [Мониторинг устройства с помощью консоли администрирования &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![PDW Admin Console Alerts](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Системные представления  
SQL Server PDW включает сложную систему представления, которые дают возможность получить подробные сведения о работоспособности устройства, состояние и производительность. Список системных представлений для отслеживания задач см.:  
  
-   [Мониторинг устройства с помощью системных представлений &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW имеет расширенную интеграцию с System Center Operations Manager. Пакеты управления для SQL Server PDW доступны для бесплатной загрузки. Дополнительные сведения об использовании System Center для мониторинга SQL Server PDW см.  
  
-   [Мониторинг устройства с помощью System Center Operations Manager &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Пользовательские решения  
Для ситуаций, когда System Center не доступен с помощью средства, мониторинга центра обработки данных можно отслеживать устройства с помощью мониторинга решения сторонних разработчиков. Установка агентов внешнего программного обеспечения в настоящее время не поддерживается в PDW, но большинство решений мониторинга поддерживает Transact\-интеграции SQL, поэтому системный администратор может реализовать прямой Transact\-SQL-запросов к вашей PDW устройство.  
  
Если решение мониторинга не поддерживает прямой Transact\-SQL-запросов, или не иметь средства мониторинга, то можно использовать скрипты для выполнения задач мониторинга, например, отправку по электронной почте при возникновении предупреждения.  Вики-сайте TechNet пример сценария мониторинга решения.  
  
-   [Power Shell примера мониторинга для SQL Server PDW](http://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Связанные задачи наблюдения  
  
|Мониторинг задач|Описание|  
|-------------------|---------------|  
|Контролировать устройства с помощью консоли администрирования.|[Мониторинг устройства с помощью консоли администрирования &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Контролировать устройства с помощью системных представлений.|[Мониторинг устройства с помощью системных представлений &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Монитор устройства с помощью System Center|[Мониторинг устройства с помощью System Center Operations Manager &#40;система платформы аналитики&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Наблюдение за состоянием устройства.|[Состояние работоспособности монитора устройства &#40;система платформы аналитики&#41;](monitor-appliance-health-state.md)|  
|Мониторинг пакетов пульса.|[Отправить данные телеметрии отзыв в корпорацию Майкрософт &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Отслеживать оповещения устройства.|[Отслеживать оповещения устройства &#40;система платформы аналитики&#41;](track-appliance-alerts.md)|  
|Определите, какой объем ресурсов уже используется.|[Просмотреть использование емкости &#40;система платформы аналитики&#41;](view-capacity-utilization.md)|  
|Определите, как часто будут опрашивать устройства.|[Определить частоту опроса &#40;система платформы аналитики&#41;](determine-polling-frequency.md)|  
|При возникновении сбоя кластера, определить, какой кластер узла не удалось.|[Определите, какой узел кластера не удалось &#40;система платформы аналитики&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Задачи управления устройством &#40;система платформы аналитики&#41;](appliance-management-tasks.md)  
  
