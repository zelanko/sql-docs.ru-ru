---
title: "dbo.slo_assignment_history (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
- slo_assignment_history_TSQL
- dbo.slo_assignment_history_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
ms.assetid: 048a6fb5-2fc2-4d12-a436-4c53ecd413f3
caps.latest.revision: "9"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fcff1c5141e6556f8cb4184284769e3be537f80a
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="dbosloassignmenthistory-azure-sql-database"></a>dbo.slo_assignment_history (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  **Это относится только к [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.**  
>   
>  Этот компонент доступен в состоянии предварительной версии. Не полагайтесь на конкретную реализацию этого компонента, так как он может быть изменен или удален в следующей версии.  
  
 Возвращает журнал назначений SLO баз данных на сервере, в том числе:  
  
-   Журнал назначений SLO баз данных на сервере.  
  
-   Время начала и окончания каждого запроса на изменение SLO баз данных.  
  
-   Все ошибки назначения SLO, содержащиеся в столбцах error_code и error_desc.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|database_name|**sysname**|Имя базы данных.|  
|database_id|**int**|Идентификатор базы данных.|  
|create_date|**datetimeoffset(7)**|Дата создания базы данных.|  
|service_objective_name|**sysname**|Имя цели уровня обслуживания (SLO).|  
|service_objective_id|**uniqueidentifier**|Идентификатор SLO.|  
|operation_id|**uniqueidentifier**|Идентификатор операции.|  
|operation_start_time|**datetimeoffset(7)**|Время начала запроса на изменение SLO базы данных.|  
|operation_end_time|**datetimeoffset(7)**|Время окончания запроса на изменение SLO базы данных.|  
|error_code|**int**|Код ошибки запроса на изменение SLO базы данных.|  
|error_desc|**nvarchar**|Описание ошибки запроса на изменение SLO базы данных.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры возвращают журнал назначений SLO базы данных для указанной базы данных.  
  
```  
SELECT *  
FROM dbo.slo_assignment_history   
WHERE database_name = '<DB NAME>’   
ORDER BY operation_start_time DESC;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Управление расширенными базами данных](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
