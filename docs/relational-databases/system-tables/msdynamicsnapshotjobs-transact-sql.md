---
title: Мсдинамикснапшотжобс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: f8822b0e7c56fe109a251365050f5aed9cdef178
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907361"
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В таблице **мсдинамикснапшотжобс** отслеживаются параметризованные сведения о фильтре строк, применяемые для создания моментального снимка отфильтрованных данных. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**удостоверения**|**int**|Идентификатор для задания моментального снимка отфильтрованных данных.|  
|**name**|**имеет sysname**|Имя задания моментального снимка отфильтрованных данных.|  
|**pubid**|**UNIQUEIDENTIFIER**|Уникальный идентификационный номер этой публикации.|  
|**job_id**|**UNIQUEIDENTIFIER**|Идентификатор задания агента SQL Server на распространителе.|  
|**agent_id**|**int**|Идентификатор агента SQL Server.|  
|**dynamic_filter_login**|**имеет sysname**|Значение, используемое для вычисления функции [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) в параметризованных фильтрах строк, определенных для публикации.|  
|**dynamic_filter_hostname**|**имеет sysname**|Значение, используемое для вычисления функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) в параметризованных фильтрах строк, определенных для публикации.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Путь к папке, откуда будут считываться файлы моментального снимка, если используется моментальный снимок отфильтрованных данных.|  
|**partition_id**|**int**|Идентификатор секции данных, которой принадлежит задание.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
