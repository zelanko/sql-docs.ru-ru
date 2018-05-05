---
title: sys.dm_exec_valid_use_hints (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
caps.latest.revision: 5
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4ef8bf4531a33ddb5fb775de12cd2ac9be11fbc0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает [используйте ПОДСКАЗКУ](../../t-sql/queries/hints-transact-sql-query.md) поддерживается Указание имен. В нем перечислены одно имя указания каждой строки.  
  
Чтобы просмотреть список всех поддерживаемых указаний в нотации используйте ПОДСКАЗКУ, используйте это динамическое административное Представление.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|имя|**sysname**|Имя подсказки.|

В разделе [подсказки в запросе](../../t-sql/queries/hints-transact-sql-query.md) описания каждой из подсказок.

Представленные в [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] с пакетом обновления 1.
  
## <a name="see-also"></a>См. также  
    
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

