---
title: Отслеживание оповещений устройства - Analytics Platform System | Документация Майкрософт
description: Отслеживание оповещений устройства в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f38f76975290538a35203ddbbed84b9354285edc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63156982"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Отслеживание оповещений устройства в Analytics Platform System
В этом разделе описывается использование консоли администрирования и системных представлений для отслеживания оповещений в устройстве SQL Server PDW.  
  
## <a name="to-track-appliance-alerts"></a>Отслеживание оповещений устройства  
SQL Server PDW создает оповещения для оборудования и программного обеспечения проблем, требующих вмешательства. Каждое оповещение содержит заголовок и описание проблемы.  
  
SQL Server PDW журналы и оповещения [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) динамического административного Представления. Система сохраняет ограничение в 10 000 оповещений и сначала удаляет старые оповещения при превышении ограничений.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Просмотр оповещений с помощью консоли администрирования  
Существует **оповещения** "Вкладка" для региона PDW и для области fabric устройства. После отработки отказа, отработка отказа событие включается в список оповещений число оповещений на странице. Имеется страница для региона PDW и для области fabric устройства. Каждая страница работоспособности имеет вкладку. Дополнительные сведения о предупреждении, щелкните **работоспособности** странице **оповещения** , а затем щелкните оповещение.  
  
![PDW Admin Console Alerts](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
На **оповещения** страницы:  
  
-   Чтобы просмотреть журнал предупреждения, щелкните **истории предупреждений проверки** ссылку.  
  
-   Чтобы просмотреть оповещения компонента и его текущие значения свойств, щелкните строку оповещения.  
  
-   Чтобы просмотреть подробные сведения об узле, вызвавшая оповещение, щелкните имя узла.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Просмотр оповещений с помощью системных представлений  
Чтобы просмотреть оповещения с помощью системных представлений, запросите [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). Это динамическое административное Представление отображаются оповещения, которые не были исправлены. Для получения справки с помощью рассмотрение предупреждений и ошибок, используйте [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) динамического административного Представления.  
  
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
[Мониторинг устройства &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
