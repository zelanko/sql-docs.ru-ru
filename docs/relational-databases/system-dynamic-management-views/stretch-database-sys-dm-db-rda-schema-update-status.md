---
title: sys. dm_db_rda_schema_update_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b74f408bdb2be61076d5034478dc6743259fed6a
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053650"
---
# <a name="stretch-database---sysdm_db_rda_schema_update_status"></a>Stretch Database-sys. dm_db_rda_schema_update_status
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Содержит по одной строке для каждой задачи обновления схемы для архива удаленных данных каждой таблицы с поддержкой растяжения в текущей базе данных. Задачи идентифицируются по идентификаторам задач.  
  
 **dm_db_rda_schema_update_status** ограничивается контекстом текущей базы данных. Убедитесь, что вы используете контекст базы данных таблицы с поддержкой Stretch, для которой требуется просмотреть состояние обновления схемы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|ИДЕНТИФИКАТОР локальной таблицы с поддержкой растяжения, для которой обновляется схема архива удаленных данных.|  
|**database_id**|**int**|Идентификатор базы данных, содержащей локальную таблицу с поддержкой растяжения.|  
|**task_id**|**bigint**|Идентификатор задачи обновления схемы удаленного архива данных.|  
|**task_type**|**int**|Тип задачи обновления схемы для архива удаленных данных.|  
|**task_type_desc**|**nvarchar**|Описание типа задачи обновления схемы для архива удаленных данных.|  
|**task_state**|**int**|Состояние задачи обновления схемы удаленного архива данных.|  
|**task_state_des**|**nvarchar**|Описание состояния задачи обновления схемы удаленного архива данных.|  
|**start_time_utc**|**datetime**|Время в формате UTC, когда было запущено обновление схемы удаленного архива данных.|  
|**end_time_utc**|**datetime**|Время (в формате UTC) завершения обновления схемы архива данных.|  
|**error_number**|**int**|Если обновление схемы удаленного архива данных завершается неудачей, номер ошибки, возникшей в результате ошибки; в противном случае значение null.|  
|**error_severity**|**int**|Если обновление схемы удаленного архива данных завершается неудачей, серьезность возникшей ошибки; в противном случае значение null.|  
|**error_state**|**int**|Если происходит сбой обновления схемы удаленного архива данных, то состояние возникшей ошибки; в противном случае значение null. Error_state указывает условие или расположение, в котором произошла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  
