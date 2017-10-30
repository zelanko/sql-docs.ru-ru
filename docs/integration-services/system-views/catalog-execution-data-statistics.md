---
title: "представлениея | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6f51407e-0e4e-4b44-af33-db14c9d40ded
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: fa1d87489ff6d0a10d95bf160ded3d038ca39d81
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogexecutiondatastatistics"></a>catalog.execution_data_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Это представление отображает строку каждый раз, когда компонент потока данных передает данные в компонент, находящийся ниже в иерархии, для выполнения данного пакета. Данные в этом представлении могут быть использованы для расчета пропускной способности данных для компонента.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|data_stats_id|**bigint**|Уникальный идентификатор данных.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|package_name|**nvarchar(260)**|Имя первого пакета, запущенного во время выполнения.|  
|task_name|**nvarchar(4000)**|Имя задачи потока данных.|  
|dataflow_path_id_string|**nvarchar(4000)**|Строка идентификации пути потока данных.|  
|dataflow_path_name|**nvarchar(4000)**|Имя пути потока данных.|  
|source_component_name|**nvarchar(4000)**|Имя компонента потока данных, который отправил данные.|  
|destination_component_name|**nvarchar(4000)**|Имя компонента потока данных, который получил данные.|  
|rows_sent|**bigint**|Число строк, отправленных из компонента источника.|  
|created_time|**datatimeoffset(7)**|Время, когда были получены значения.|  
|execution_path|**nvarchar(max)**|Путь выполнения компонента.|  
  
## <a name="remarks"></a>Замечания  
  
-   Если существует несколько выходов из компонента, добавляется строка для каждого выхода.  
  
-   По умолчанию, когда начинается выполнение, сведения о количестве переданных строк не регистрируются.  
  
-   Чтобы просмотреть эти данные для выполнения данного пакета, установите уровень ведения журнала на **Verbose**. Дополнительные сведения см. в разделе [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  

