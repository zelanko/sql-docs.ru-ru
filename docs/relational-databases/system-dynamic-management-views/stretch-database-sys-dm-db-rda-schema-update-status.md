---
title: sys.dm_db_rda_schema_update_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbd99f97902dbbd3c097b76b1f119f400f97c6f6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420063"
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Stretch Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой задачи обновления схемы для архива удаленных данных из каждой таблицы с поддержкой Stretch в текущей базе данных. Задачи идентифицируются по их идентификаторов задач.  
  
 **dm_db_rda_schema_update_status** ограничивается в контексте текущей базы данных. Убедитесь, что вы находитесь в контексте базы данных, для которого вы хотите увидеть состояние обновления схемы таблицы с включенным Stretch.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Идентификатор локальной которого удаленного архива данных схемы таблицы с включенным Stretch обновляется.|  
|**database_id**|**int**|Идентификатор базы данных, которая содержит таблицу локальной поддержкой Stretch.|  
|**TASK_ID**|**bigint**|Идентификатор задачи обновления схемы архив удаленных данных.|  
|**task_type**|**int**|Тип задачи обновления схемы архив удаленных данных.|  
|**task_type_desc**|**nvarchar**|Описание типа задачи обновления схемы архив удаленных данных.|  
|**task_state**|**int**|Состояние задачи обновления схемы архив удаленных данных.|  
|**task_state_des**|**nvarchar**|Описание состояния задачи обновления схемы архив удаленных данных.|  
|**start_time_utc**|**datetime**|Время в формате UTC, по которому удаленного архива данных начато обновление схемы.|  
|**end_time_utc**|**datetime**|Время в формате UTC, по которому удаленного архива данных обновление схемы завершено.|  
|**error_number**|**int**|Если происходит сбой обновления схемы архив удаленных данных, номер ошибки, возникшей; в противном случае — значение null.|  
|**error_severity**|**int**|Если происходит сбой обновления схемы архив удаленных данных, уровень серьезности ошибки, возникшей; в противном случае — значение null.|  
|**error_state**|**int**|Если происходит сбой обновления схемы архив удаленных данных, состояние ошибки, возникшей; в противном случае — значение null. Error_state указывает условие или расположение, где произошла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
