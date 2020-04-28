---
title: Мониторинг устройства
description: В этом руководством по мониторингу устройства описываются средства и задачи для мониторинга системного устройства аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: cec604ff1a93213fc6308455cadda90e6efa2d61
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401426"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Мониторинг устройств для системы аналитики платформы
В этом руководством по мониторингу устройства описываются средства и задачи для мониторинга системного устройства аналитики.  
  
## <a name="monitoring-basics-and-tools"></a><a name="Basics"></a>Основы и средства мониторинга  
Значения и сведения, которые можно отслеживать на SQL Server PDW устройстве, являются обширными. Например, ниже приведены типичные задачи мониторинга.  
  
-   Проверьте наличие предупреждений, выпущенных SQL Server PDW.  
  
-   Наблюдение за неисправным оборудованием.  
  
-   Наблюдение за проблемами сетевого подключения.  
  
-   Проверка на наличие ошибок, возвращенных пользователям во время обработки запроса.  
  
-   Просмотр числа активных в данный момент сеансов и запросов.  
  
-   Проверьте состояние загрузки, резервного копирования и восстановления.  
  
### <a name="appliance-monitoring-tools"></a>Средства мониторинга устройств  
Для мониторинга устройства доступно несколько средств.  
  
Административная консоль  
SQL Server PDW имеет консоль администрирования. Это веб-средство, которое отображает сведения о запросах, загрузках, резервном копировании и восстановлении, блокировках, сеансах, предупреждениях и состоянии устройства. Консоль администрирования работает на устройстве; Пользователи подключаются к консоли администрирования через Internet Explorer. Дополнительные сведения можно найти в разделе  
  
-   [Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![Предупреждения консоли администрирования PDW](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Системные представления  
SQL Server PDW включает в себя комплексные системные представления, позволяющие получать подробные сведения о работоспособности, состоянии и производительности устройства. Список системных представлений для наблюдения за задачами см. в следующих статьях:  
  
-   [Мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW имеет обширную интеграцию с Operations Manager Systems Center. Пакеты управления для SQL Server PDW доступны для бесплатной загрузки. Дополнительные сведения об использовании System Center для мониторинга SQL Server PDW см. в следующих статьях:  
  
-   [Мониторинг устройства с помощью системы System Center Operations Manager &#40;Analytics Platform&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Пользовательские решения  
В ситуациях, когда System Center недоступен в средствах мониторинга центра обработки данных, вы можете отслеживать устройство с помощью решения для мониторинга сторонних производителей. Установка внешних агентов программного обеспечения в настоящее время не поддерживается в PDW, но большинство решений мониторинга\-поддерживают интеграцию с SQL, поэтому системный администратор может реализовать прямые\-запросы TRANSACT SQL к устройству PDW.  
  
Если решение для мониторинга не поддерживает прямые запросы Transact\-SQL или у вас нет средства мониторинга, то можно использовать сценарии для выполнения задач мониторинга, таких как отправка сообщения электронной почты при возникновении предупреждения.  На вики-сайте TechNet есть пример решения по мониторингу сценариев.  
  
-   [Пример мониторинга PowerShell для SQL Server PDW](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="related-monitoring-tasks"></a><a name="Tasks"></a>Связанные задачи мониторинга  
  
|Задача мониторинга|Описание|  
|-------------------|---------------|  
|Мониторинг устройства с помощью консоли администрирования.|[Мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Мониторинг устройства с помощью системных представлений.|[Мониторинг устройства с помощью системных представлений &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Мониторинг устройства с помощью System Center|[Мониторинг устройства с помощью системы System Center Operations Manager &#40;Analytics Platform&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Наблюдение за состоянием устройства.|[Мониторинг состояния работоспособности устройства &#40;&#41;платформы аналитики](monitor-appliance-health-state.md)|  
|Мониторинг пульса.|[Отправка отзывов телеметрии в Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Следите за оповещениями устройства.|[Мониторинг оповещений устройства &#40;&#41;платформы аналитики](track-appliance-alerts.md)|  
|Определите, сколько емкости используется.|[Просмотр использования емкости &#40;аналитики платформа&#41;](view-capacity-utilization.md)|  
|Определите частоту опроса устройства.|[Определение частоты опроса &#40;&#41;системы аналитики](determine-polling-frequency.md)|  
|При возникновении сбоя кластера определите, какой узел кластера завершился сбоем.|[Определите, какой узел кластера завершился сбоем &#40;&#41;системы аналитики](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>См. также:  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Задачи управления устройством &#40;&#41;платформы аналитики](appliance-management-tasks.md)  
  
