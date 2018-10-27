---
title: sys.dm_exec_valid_use_hints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 628ef2cde5b345366a7ba0fb7ffff6c8e5143a0c
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806694"
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает [USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint) поддерживается Указание имен. В ней перечислены одно указание имя каждой строки.  
  
Используйте это динамическое административное Представление, чтобы просмотреть список всех поддерживаемых указаний в нотации USE HINT.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Имя подсказки.|

См. в разделе [указания запросов](../../t-sql/queries/hints-transact-sql-query.md#use_hint) описания каждого подсказку.

Представленные в [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] с пакетом обновления 1.
  
## <a name="see-also"></a>См. также  
    
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

