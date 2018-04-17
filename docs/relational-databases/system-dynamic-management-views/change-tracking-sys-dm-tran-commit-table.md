---
title: sys.dm_tran_commit_table (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_tran_commit_table
- dm_tran_commit_table_TSQL
- sys.dm_tran_commit_table
- sys.dm_tran_commit_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_commit_table dynamic management view
ms.assetid: 732d23c5-1f6c-4e96-bc85-8f29b520cf0e
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7ef5171ec533bd912c14d3623a9c01e93d79edf2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="change-tracking---sysdmtrancommittable"></a>Отслеживание - изменить sys.dm_tran_commit_table
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  В этой таблице отображается одна строка для каждой транзакции, зафиксированной для таблицы, которая обрабатывается средством отслеживания изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Административное представление sys.dm_tran_commit_table, которое предоставлено в целях поддержки, позволяет получить доступ к информации, связанной с транзакцией, которую система отслеживания изменений хранит в системной таблице sys.syscommittab. Таблица sys.syscommittab позволяет выполнять эффективное постоянное сопоставление идентификатора транзакции, относящегося к конкретной базе данных, с регистрационным номером транзакции в журнале (номером LSN) фиксации транзакции и отметкой времени фиксации. Данные, которые хранятся в таблице sys.syscommittab table и выведены в административном представлении, удаляются по истечении срока хранения, задаваемого при настройке отслеживания изменений.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_commit_table**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|Монотонно возрастающее число, которое служит в качестве относящейся к конкретной базе данных отметки времени для каждой зафиксированной транзакции.|  
|xdes_id|**bigint**|Зависящий от базы данных внутренний идентификатор транзакции.|  
|commit_lbn|**bigint**|Номер блока журнала, который содержит запись журнала фиксации транзакции.|  
|commit_csn|**bigint**|Зависящий от экземпляра порядковый номер фиксации транзакции.|  
|commit_time|**smalldatetime**|Время фиксации транзакции.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Об отслеживании изменений (SQL Server)](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


