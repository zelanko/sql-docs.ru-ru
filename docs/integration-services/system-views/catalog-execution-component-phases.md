---
title: "Catalog.execution_component_phases | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 07a9a163-4787-40f7-b371-ac5c6cb4b095
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: b3459ce6d7e9eb0b9580ffa54e3b87e16f3e8fb0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogexecutioncomponentphases"></a>catalog.execution_component_phases
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает время, затраченное компонентом потока данных на каждом этапе выполнения.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|phase_stats_id|**bigint**|Уникальный идентификатор (ID) этапа.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|package_name|**nvarchar(260)**|Имя первого пакета, запущенного во время выполнения.|  
|task_name|**nvarchar(4000)**|Имя задачи потока данных.|  
|subcomponent_name|**nvarchar(4000)**|Имя компонента потока данных.|  
|этап|**nvarchar(128)**|Имя этапа выполнения.|  
|start_time|**DateTimeOffset(7)**|Время начала этапа.|  
|end_time|**DateTimeOffset(7)**|Время окончания этапа.|  
|execution_path|**nvarchar(max)**|Путь выполнения задачи потока данных.|  
  
## <a name="remarks"></a>Замечания  
 Это представление отображает строку для каждого этапа выполнения компонента потока данных, такого как Validate, Pre-Execute, Post-Execute, PrimeOutput и ProcessInput. Каждая строка отображает время начала и окончания для конкретного этапа выполнения.  
  
## <a name="example"></a>Пример  
 В следующем примере используется представление catalog.execution_component_phases для нахождения общего времени, определенного пакета потратил на выполнение всех фаз (**active_time**) и общее затраченное время для пакета (**total_time**).  
  
> [!WARNING]  
>  Представление catalog.execution_component_phases предоставляет эти сведения, если в качестве уровня ведения журнала выполнения пакетов задано значение Performance или Verbose. Дополнительные сведения см. в разделе [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).  
  
```sql
use SSISDB  
select package_name, task_name, subcomponent_name, execution_path,  
    SUM(DATEDIFF(ms,start_time,end_time)) as active_time,  
    DATEDIFF(ms,min(start_time), max(end_time)) as total_time  
from catalog.execution_component_phases  
where execution_id = 1841  
group by package_name, task_name, subcomponent_name, execution_path  
order by package_name, task_name, subcomponent_name, execution_path  
```  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
