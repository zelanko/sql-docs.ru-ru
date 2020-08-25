---
title: Мониторинг работоспособности устройства
description: Мониторинг состояния устройства системы аналитики с помощью консоли администрирования или непосредственное выполнение запросов к динамическим административным представлениям хранилища данных.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b99123f81fcdddd74dc72d485d97e428ca59ed84
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400995"
---
# <a name="monitor-appliance-health-state"></a>Мониторинг состояния работоспособности устройства
В этой статье объясняется, как отслеживать состояние устройства системы аналитики с помощью консоли администрирования или путем прямого запроса к динамическим административным представлениям параллельного хранилища данных. 
  
## <a name="to-monitor-the-appliance-state"></a>Мониторинг состояния устройства  
Системный администратор может использовать консоль администрирования или динамические административные представления SQL Server PDW (DMV) для получения полной иерархии узлов, компонентов и программного обеспечения. На следующей схеме представлено общее представление о компонентах, которые SQL Server PDW мониторов.  
  
![Общие сведения о мониторинге](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Мониторинг состояния компонента с помощью консоли администрирования  
Чтобы получить состояние компонента с помощью консоли администрирования, выполните следующие действия.  
  
1.  Перейдите на вкладку **состояние устройства** .  
  
2.  На странице Состояние устройства щелкните конкретный узел, чтобы просмотреть сведения об узле.  
  
    ![Состояние консоли администрирования PDW](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Мониторинг состояния компонента с помощью системных представлений  
Чтобы получить состояние компонента с помощью системных представлений, используйте представление [sys. dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Например, следующий запрос получает сведения о состоянии всех компонентов.  
  
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
  
Для свойства Status могут возвращаться следующие значения:  
  
-   ОК  
  
-   Некритическая  
  
-   Критические важное  
  
-   Неизвестно  
  
-   Не поддерживается  
  
-   Недостижимо  
  
-   восстановление не происходит.  
  
Чтобы просмотреть все свойства всех компонентов, удалите `WHERE  p.property_name = 'Status'` предложение.  
  
В столбце **[update_time]** отображается время последнего опроса компонента агентами исправности SQL Server PDW.  
  
> [!CAUTION]  
> Не забудьте исследовать проблему, если компонент не был опрошен в течение 5 минут или больше. может быть оповещение, указывающее на ошибку в пульсах программного обеспечения.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Мониторинг устройств &#40;системная платформа аналитики&#41;](appliance-monitoring.md)  
  
