---
description: Представления каталога Azure Synapse Analytics и Parallel Data Warehouse
title: Представления каталога
titleSuffix: Azure Synapse Analytics and Parallel Data Warehouse
ms.date: 10/29/2019
ms.service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ef6f58e2-0162-4bb2-951a-a786da7453e4
author: julieMSFT
ms.author: jrasnick
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.custom: seo-dt-2019
ms.openlocfilehash: 326d2c6f29f89af63037a0ca3d9e5111b83c828d
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97643411"
---
# <a name="azure-synapse-analytics-and-parallel-data-warehouse-catalog-views"></a>Представления каталога Azure Synapse Analytics и Parallel Data Warehouse

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

 В этом разделе перечислены [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] представления каталога и.  
  
## <a name="sssdw-and-sspdw-catalog-views"></a>Представления каталога [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующие представления каталога применимы к [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] :  
  
 [sys.pdw_column_distribution_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-column-distribution-properties-transact-sql.md)  
  
 [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md)  
  
 [sys.pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)  
  
 [sys.pdw_loader_backup_run_details (Transact-SQL)](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
 [sys.pdw_loader_backup_runs (Transact-SQL)](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)  
  
 [sys.pdw_nodes_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-columns-transact-sql.md)  
  
 [sys.pdw_nodes_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-indexes-transact-sql.md)  
  
 [sys.pdw_nodes_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-partitions-transact-sql.md)  
  
 [sys.pdw_nodes_pdw_physical_databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
 [sys.pdw_nodes_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-tables-transact-sql.md) 

 [sys.pdw_replicated_table_cache_state (Transact-SQL)](sys-pdw-replicated-table-cache-state-transact-sql.md) 
  
 [sys.pdw_table_distribution_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-distribution-properties-transact-sql.md)  
  
 [sys.pdw_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md) 

## <a name="sssdw-catalog-views"></a>[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Представления каталога

 Следующие представления каталога применимы [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] только к:

 [sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](./sys-pdw-materialized-view-column-distribution-properties-transact-sql.md?view=azure-sqldw-latest&preserve-view=true) 

 [sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](./sys-pdw-materialized-view-distribution-properties-transact-sql.md?view=azure-sqldw-latest&preserve-view=true) 

 [sys.pdw_materialized_view_mappings &#40;&#41;Transact-SQL ](./sys-pdw-materialized-view-mappings-transact-sql.md?view=azure-sqldw-latest&preserve-view=true) (Предварительная версия)

 [sys.pdw_permanent_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-permanent-table-mappings-transact-sql.md)

 [sys.workload_management_workload_classifier_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifier-details-transact-sql.md)
  
 [sys.workload_management_workload_classifiers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifiers-transact-sql.md)
  
 [sys.workload_management_workload_groups &#40;Transact-SQL&#41;](./sys-workload-management-workload-groups-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)

## <a name="sspdw-catalog-views"></a>[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] Представления каталога

 Следующие представления каталога применимы [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] только к:

 [sys.pdw_database_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
 [sys.pdw_diag_event_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-diag-event-properties-transact-sql.md)  
  
 [sys.pdw_diag_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-diag-events-transact-sql.md)  
  
 [sys.pdw_diag_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-diag-sessions-transact-sql.md)  
  
 [sys.pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)  
  
 [sys.pdw_health_component_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-groups-transact-sql.md)  
  
 [sys.pdw_health_component_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md)  
  
 [sys.pdw_health_component_status_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-status-mappings-transact-sql.md)  
  
 [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)  
  
 [sys.pdw_loader_run_stages (Transact-SQL)](../../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
