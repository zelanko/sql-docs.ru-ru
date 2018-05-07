---
title: MSdynamicsnapshotjobs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdynamicsnapshotjobs_TSQL
- MSdynamicsnapshotjobs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotjobs system table
ms.assetid: 4f36a325-0e3c-46c4-aeeb-416346cce0bc
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8cdfc74bad45bcb3e77bfdf8b438df45e1491633
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdynamicsnapshotjobs** таблица отслеживает информацию параметризованного фильтра строк применяется для создания моментального снимка отфильтрованных данных. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор для задания моментального снимка отфильтрованных данных.|  
|**name**|**sysname**|Имя задания моментального снимка отфильтрованных данных.|  
|**pubid**|**uniqueidentifier**|Уникальный идентификационный номер этой публикации.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания агента SQL Server на распространителе.|  
|**agent_id**|**int**|Идентификатор агента SQL Server.|  
|**dynamic_filter_login**|**sysname**|Значение, используемое для вычисления [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) функции в параметризованных фильтрах строк, определенных для публикации.|  
|**dynamic_filter_hostname**|**sysname**|Значение, используемое для вычисления [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) функции в параметризованных фильтрах строк, определенных для публикации.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Путь к папке, откуда будут считываться файлы моментального снимка, если используется моментальный снимок отфильтрованных данных.|  
|**partition_id**|**int**|Идентификатор секции данных, которой принадлежит задание.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
