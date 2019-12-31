---
title: Отслеживание оповещений устройства
description: Мониторинг оповещений устройства в системе платформы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 03568666367bf6273f197994f572bbbbd62bb42e
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399943"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Мониторинг оповещений устройства в системе платформы аналитики
В этом разделе объясняется, как использовать консоль администрирования и системные представления для мониторинга предупреждений в SQL Server PDW устройстве.  
  
## <a name="to-track-appliance-alerts"></a>Для трассировки оповещений устройства  
SQL Server PDW создает предупреждения о проблемах с оборудованием и программным обеспечением, требующих внимания. Каждое оповещение содержит заголовок и описание проблемы.  
  
SQL Server PDW журналы оповещений в динамическом административном [представлении sys. dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) . Система оставляет ограничение в 10 000 оповещений и удаляет самое старое предупреждение, когда превышено ограничение.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Просмотр предупреждений с помощью консоли администрирования  
Имеется вкладка **предупреждения** для региона PDW и для области структуры устройства. После отработки отказа событие отработки отказа включается в число оповещений на странице. Существует страница для региона PDW и для региона структуры устройства. Каждая страница работоспособности имеет вкладку. Чтобы получить дополнительные сведения о предупреждении, щелкните страницу **работоспособность** , вкладку **оповещения** и щелкните оповещение.  
  
![Предупреждения консоли администрирования PDW](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
На странице **оповещения** выполните следующие действия.  
  
-   Чтобы просмотреть журнал предупреждений, щелкните ссылку **Просмотр журнала предупреждений** .  
  
-   Чтобы просмотреть компонент оповещения и его текущие значения свойств, щелкните строку предупреждения.  
  
-   Чтобы просмотреть сведения об узле, вызвавшем оповещение, щелкните имя узла.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Просмотр предупреждений с помощью системных представлений  
Чтобы просмотреть предупреждения с помощью системных представлений, запросите представление [sys. dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). В этом динамическом административном отображении отображаются предупреждения, которые не были исправлены. Чтобы получить справку по классифицированию предупреждений и ошибок, используйте динамическое административное представление [sys. dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) .  
  
Ниже приведен пример общего запроса для просмотра текущих предупреждений.  
  
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
[Мониторинг устройств &#40;системная платформа аналитики&#41;](appliance-monitoring.md)  
  
