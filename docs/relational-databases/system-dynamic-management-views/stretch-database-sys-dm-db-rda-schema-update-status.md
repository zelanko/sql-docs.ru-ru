---
title: sys.dm_db_rda_schema_update_status (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b694361a46673208e52134e9c5becf2e491c9584
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>База данных - Stretch sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой задачи обновления схемы для архива удаленных данных из каждой таблицы с включенным Stretch в текущей базе данных. Задачи идентифицируются по их идентификаторам задачи.  
  
 **dm_db_rda_schema_update_status** ведется в контексте текущей базы данных. Убедитесь, что контекст базы данных, для которого вы хотите увидеть состояние обновления схемы таблицы с включенным Stretch.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Идентификатор локальной которого удаленного архива данных схемы таблицы с включенным Stretch обновляется.|  
|**database_id**|**int**|Идентификатор базы данных, которая содержит локальные таблицы с поддержкой Stretch.|  
|**TASK_ID**|**bigint**|Идентификатор задачи обновления схемы архив удаленных данных.|  
|**task_type**|**int**|Тип задачи обновления схемы архив удаленных данных.|  
|**task_type_desc**|**nvarchar**|Описание типа задачи обновления схемы архив удаленных данных.|  
|**task_state**|**int**|Состояние задачи обновления схемы архив удаленных данных.|  
|**task_state_des**|**nvarchar**|Описание состояния задачи обновления схемы архив удаленных данных.|  
|**start_time_utc**|**datetime**|Время в формате UTC, по которому удаленного архива данных начато обновление схемы.|  
|**end_time_utc**|**datetime**|Время в формате UTC, по которому удаленного архива данных обновление схемы завершено.|  
|**error_number**|**int**|Если происходит сбой обновления схемы архив удаленных данных, номер ошибки для ошибки, возникшей; в противном случае — значение null.|  
|**error_severity**|**int**|Если происходит сбой обновления схемы архив удаленных данных, серьезность ошибки, возникшей; в противном случае — значение null.|  
|**error_state**|**int**|Если происходит сбой обновления схемы архив удаленных данных, состояние ошибки, возникшей; в противном случае — значение null. Функция error_state указывает условие или расположение, где произошла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
