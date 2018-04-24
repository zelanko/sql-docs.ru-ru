---
title: Просмотреть использование емкости в Analytics Platform System | Документы Microsoft
description: Просмотр использования емкости в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: fcd440f3add9ff6823c9104fc94af736d3fdee4e
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="view-capacity-utilization-in-analytics-platform-system"></a>Просмотр использования емкости в система платформы аналитики
В этом разделе описывается просмотр степень использования производительности в SQL Server PDW appliance.  
  
## <a name="to-view-capacity-utilization-by-using-admin-console"></a>Чтобы просмотреть использование ресурсов с помощью консоли администрирования  
Чтобы просмотреть пространство, используемое, откройте консоль администрирования и нажмите кнопку **хранения** вкладки. Отсутствует **хранения** вкладке регион PDW и регион HDI.  
  
![Хранилище консоли администрирования PDW](./media/view-capacity-utilization/SQL_Server_PDW_AdminConsol_StorageV2.png "SQL_Server_PDW_AdminConsol_StorageV2")  
  
## <a name="to-view-capacity-utilization-by-using-queries"></a>Чтобы просмотреть использование ресурсов с помощью запросов  
Чтобы понять, если узел работает в условиях нехватки места на, система мониторинга работоспособности SQL Server PDW уже отслеживает свободное пространство для всех томов в каждом узле.  
  
Если свободное пространство в томе с падает ниже 30%, SQL Server PDW приводит к возникновению ошибки **предупреждение** предупреждения в [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md).  Предупреждение остается, пока не станет доступным свободное пространство.  
  
Если свободное пространство в томе с опустится ниже 10%, SQL Server PDW приводит к возникновению ошибки **критические** предупреждение. Это считается критическое, поскольку запросов может завершиться ошибкой, если они вызывают увеличение базы данных.  
  
Чтобы получить использование тома, см. следующий пример.  
  
```sql  
SELECT   
    space.[pdw_node_id] ,  
    space.[node_name] ,  
    MAX(space.[volume_name]) AS 'volume_name' ,  
    MAX(space.[volume_size_mb]) AS 'volume_size_mb' ,  
    MAX(space.[free_space_mb]) AS 'free_space_mb' ,  
   (MAX(space.[volume_size_mb]) - MAX(space.[free_space_mb])) AS 'space_utilized'  
FROM (  
    SELECT   
        s.[pdw_node_id],  
        n.[name] AS [node_name],  
        (CASE WHEN p.property_name = 'volume_name'   
            THEN s.[property_value] ELSE NULL END) AS 'volume_name' ,  
        (CASE WHEN p.property_name = 'volume_size'   
            THEN (CAST(ISNULL(s.[property_value], '0') AS BIGINT)/1024/1024)   
            ELSE 0 END) AS 'volume_size_mb' ,  
        (CASE WHEN p.property_name = 'volume_free_space'   
            THEN (CAST(ISNULL(s.[property_value], '0') AS BIGINT)/1024/1024)   
            ELSE 0 END) AS 'free_space_mb' , s.[component_instance_id]  
    FROM [sys].[dm_pdw_component_health_status] AS s  
        JOIN sys.dm_pdw_nodes AS n   
            ON s.[pdw_node_id] = n.[pdw_node_id]  
        JOIN [sys].[pdw_health_components] AS c   
            ON s.[component_id] = c.[component_id]  
        JOIN [sys].[pdw_health_component_properties] AS p   
            ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
    WHERE  
        c.[Component_name] = 'Volume'  
        AND p.[property_name] IN ('volume_name', 'volume_free_space', 'volume_size')  
    ) AS space  
GROUP BY space.[pdw_node_id] , space.[node_name] , space.[component_instance_id]  
ORDER BY space.[pdw_node_id], MAX(space.[volume_name]);  
```  
  
Чтобы получить пространства, занимаемого базами данных на узлах устройства, см. следующий пример.  
  
```sql  
SELECT   
    [pdw_node_id],   
    [db_name],   
    SUM(CASE WHEN [file_type] = 'DATA' THEN [value_MB] ELSE 0 END) AS [DataSizeMB],  
    SUM(CASE WHEN [file_type] = 'LOG' THEN [value_MB] ELSE 0 END) AS [LogSizeMB],  
    SUM([value_MB]) AS [TotalMB]  
FROM (  
    SELECT   
        pc.[pdw_node_id],   
        RTRIM(pc.[counter_name]) AS [counter_name],   
        ISNULL(d.[name], pc.[instance_name]) AS [db_name],   
        pc.[cntr_value]/1024 AS [value_MB],  
        CASE   
            WHEN [counter_name] LIKE 'Data File(s) Size%'   
            THEN 'DATA'   
            ELSE 'LOG'   
        END AS [file_type]  
    FROM sys.dm_pdw_nodes_os_performance_counters AS pc  
        LEFT JOIN sys.pdw_database_mappings AS dm   
            ON pc.instance_name = dm.physical_name  
        INNER JOIN sys.databases AS d   
            ON d.database_id = dm.database_id  
    WHERE   
        ([counter_name] LIKE 'Log File(s) Size%'  
             OR [counter_name] LIKE 'Data File(s) Size%')  
        AND (d.[name] <> dm.[physical_name]   
             OR pc.[instance_name] = 'tempdb')  
) AS db  
GROUP BY [pdw_node_id], [db_name]  
ORDER BY [db_name], [pdw_node_id];  
```  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Мониторинг устройства &#40;система платформы аналитики&#41;](appliance-monitoring.md)  
  
