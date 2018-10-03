---
title: MSdynamicsnapshotjobs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotjobs_TSQL
- MSdynamicsnapshotjobs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotjobs system table
ms.assetid: 4f36a325-0e3c-46c4-aeeb-416346cce0bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08a912d4027dc74f06455b448c68e58323f4d78c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751644"
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
  
  
