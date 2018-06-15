---
title: Отслеживать оповещения appliance - система платформы аналитики | Документы Microsoft
description: Отслеживать оповещения устройства в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 82803e6f20e4a710f317e2e7a541c4a1c72ed08d
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539274"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Отслеживать оповещения устройства в система платформы аналитики
В этом разделе описывается использование консоли администрирования и системных представлений для отслеживания оповещений в в SQL Server PDW appliance.  
  
## <a name="to-track-appliance-alerts"></a>Чтобы отслеживать устройства предупреждения  
SQL Server PDW создает оповещения о проблемах оборудования и программного обеспечения, которые нужно обратить внимание. Каждое предупреждение имеет заголовок и описание проблемы.  
  
SQL Server PDW журналы и оповещения [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) динамического административного Представления. Система сохраняет ограничение в 10 000 оповещений и сначала удаляет старые предупреждение при превышении этого ограничения.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Просмотр оповещений с помощью консоли администрирования  
Отсутствует **оповещения** область PDW области HDI, а также области структуры устройства. После перехода на другой ресурс, переход на другой ресурс событие включается в число оповещений на странице. Имеется страница PDW области, области HDI и области структуры устройства. Каждая страница работоспособности имеет вкладки. Дополнительные сведения о предупреждении щелкните **работоспособности** страницы, **оповещения** , а затем щелкните оповещение.  
  
![PDW Admin Console Alerts](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
На **оповещения** страницы:  
  
-   Чтобы просмотреть журнал предупреждения, щелкните на **истории предупреждений проверки** ссылку.  
  
-   Чтобы просмотреть предупреждения компонента и его текущего значения свойства, щелкните строку предупреждения.  
  
-   Чтобы просмотреть сведения об узле, вызвавшее предупреждение, щелкните имя узла.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Просмотр оповещений с помощью системных представлений  
Просмотр оповещений с помощью системных представлений, запросов [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). Это динамическое административное Представление отображаются оповещения, которые не были исправлены. Для получения справки по рассмотрение предупреждения и ошибки, используйте [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) динамического административного Представления.  
  
Ниже приведен один из распространенных запросов для просмотра текущих предупреждений.  
  
```sql  
SELECT   
    aa.[pdw_node_id],  
    n.[name] AS [node_name],  
    g.[group_name] ,  
    c.[component_name] ,  
    aa.[component_instance_id] ,   
    a.[alert_name] ,  
    a.[state] ,  
    a.[severity] ,  
    aa.[current_value] ,  
    aa.[previous_value] ,  
    aa.[create_time] ,  
    a.[description]   
FROM [sys].[dm_pdw_component_health_active_alerts] AS aa  
    INNER JOIN sys.dm_pdw_nodes AS n   
        ON aa.[pdw_node_id] = n.[pdw_node_id]  
    INNER JOIN [sys].[pdw_health_components] AS c   
        ON aa.[component_id] = c.[component_id]  
    INNER JOIN [sys].[pdw_health_component_groups] AS g   
        ON c.[group_id] = g.[group_id]  
    INNER JOIN [sys].[pdw_health_alerts] AS a   
        ON aa.[alert_id] = a.[alert_id] and aa.[component_id] = c.[component_id]  
ORDER BY  
    a.alert_id ,  
    aa.[pdw_node_id];  
```  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Мониторинг устройства &#40;система платформы аналитики&#41;](appliance-monitoring.md)  
  
