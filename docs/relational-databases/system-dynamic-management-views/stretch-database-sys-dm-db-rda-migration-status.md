---
title: "sys.dm_db_rda_migration_status (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3b4687e98a7fb917390e7ca8811c50bf543744c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>База данных - Stretch sys.dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого пакета перенесенных данных из каждой таблицы с включенным Stretch на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пакеты определяются по времени начала и времени окончания.  
  
 **sys.dm_db_rda_migration_status** ведется в контексте текущей базы данных. Убедитесь, что находитесь в контексте базы данных включить растяжение таблиц, для которых требуется просмотреть состояние миграции.  
  
 В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], выходные данные **sys.dm_db_rda_migration_status** ограничено до 200 строк.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Идентификатор таблицы, из которого были перенесены строки.|  
|**database_id**|**int**|Идентификатор базы данных, из которого были перенесены строки.|  
|**migrated_rows**|**bigint**|Число строк, переносятся в этом пакете.|  
|**start_time_utc**|**datetime**|В формате UTC начала пакета.|  
|**end_time_utc**|**datetime**|Время в формате UTC, по которому завершения пакета.|  
|**error_number**|**int**|Если происходит сбой пакета, номер ошибки для ошибки, возникшей; в противном случае — значение null.|  
|**error_severity**|**int**|Если происходит сбой пакета, серьезность ошибки, возникшей; в противном случае — значение null.|  
|**error_state**|**int**|Если происходит сбой пакета, состояние ошибки, возникшей; в противном случае — значение null.<br /><br /> **Error_state** указывает условие или расположение, где произошла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
