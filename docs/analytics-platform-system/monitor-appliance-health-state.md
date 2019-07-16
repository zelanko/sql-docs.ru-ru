---
title: Мониторинг работоспособности устройства - Analytics Platform System
description: Как отслеживать состояние устройства система Analytics Platform System, с помощью консоли администрирования, или путем непосредственного запроса к динамическим административным представлениям Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c69e46ad6a37a17a12c37f83625b5c7f6eaf8078
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960617"
---
# <a name="monitor-appliance-health-state"></a>Состояние работоспособности монитора устройства
В этой статье объясняется, как осуществлять мониторинг состояния устройства система Analytics Platform System, с помощью консоли администрирования, или путем непосредственного запроса к динамическим административным представлениям Parallel Data Warehouse. 
  
## <a name="to-monitor-the-appliance-state"></a>Чтобы отслеживать состояние устройства  
Системный администратор может использовать консоль администратора или SQL Server PDW динамические административные представления (DMV) для получения полную иерархию узлов, компоненты и программного обеспечения. Следующая диаграмма представляет общее понимание компонентов, которые отслеживает SQL Server PDW.  
  
![Общие сведения о мониторинге](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Мониторинг состояния компонента с помощью консоли администрирования  
Чтобы получить состояние компонента с помощью консоли администрирования:  
  
1.  Щелкните **состояние устройства** вкладки.  
  
2.  На странице "Состояние устройства" щелкните конкретный узел, чтобы просмотреть сведения об узле.  
  
    ![PDW Admin Console State](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Мониторинг состояния компонента с помощью системных представлений  
Чтобы получить состояние компонента с помощью системных представлений, используйте [sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Например следующий запрос получает состояние для всех компонентов.  
  
```sql  
SELECT   
   s.[pdw_node_id],  
   n.[name] as [node_name],  
   n.[address] ,  
   g.[group_id] ,  
   g.[group_name] ,  
   c.[component_id] ,  
   c.[component_name] ,  
   s.[component_instance_id] ,   
   p.[property_name] ,  
   s.[property_value] ,  
   s.[update_time]  
FROM [sys].[dm_pdw_component_health_status] AS s  
JOIN sys.dm_pdw_nodes AS n   
   ON s.[pdw_node_id] = n.[pdw_node_id]  
JOIN [sys].[pdw_health_components] AS c   
   ON s.[component_id] = c.[component_id]  
JOIN [sys].[pdw_health_component_groups] AS g   
   ON c.[group_id] = g.[group_id]  
JOIN [sys].[pdw_health_component_properties] AS p   
   ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
WHERE p.property_name = 'Status'  
ORDER BY  
   s.[pdw_node_id],  
   g.[group_name] ,   
   s.[component_instance_id] ,  
   c.[component_name] ,   
   p.[property_name];  
```  
  
Возможные значения, возвращаемые для свойства Status::  
  
-   ОК  
  
-   Некритическая  
  
-   Critical  
  
-   Неизвестно  
  
-   Не поддерживается  
  
-   Недоступен  
  
-   Неустранимая  
  
Чтобы просмотреть все свойства для всех компонентов, удалите `WHERE  p.property_name = 'Status'` предложение.  
  
**[Update_time]** столбце указывается время последнего опроса компонент работоспособности агентов, SQL Server PDW.  
  
> [!CAUTION]  
> Не забудьте определить причину проблемы, компонент не был опрос на 5 минут или больше; может быть оповещение, которое говорит о проблемах с пульса программного обеспечения.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройства &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
