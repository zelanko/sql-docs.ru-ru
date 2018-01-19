---
title: "Агрегатные функции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/16/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 74cc3903f4d5e10718c2d4488e4c3b8da4448b80
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="aggregate-functions-transact-sql"></a>Агрегатные функции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Агрегатные функции выполняют вычисление на наборе значений и возвращают одиночное значение. Агрегатные функции, за исключением COUNT, не учитывают значения NULL. Агрегатные функции часто используются в выражении GROUP BY инструкции SELECT.
  
Все агрегатные функции являются детерминированными. Это означает, что агрегатные функции возвращают одну и ту же величину при каждом их вызове на одном и том же наборе входных значений. Дополнительные сведения о детерминизме функций см. в разделе [функций](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). [Предложение OVER](../../t-sql/queries/select-over-clause-transact-sql.md) может следовать за всеми агрегатными функциями, кроме GROUPING или GROUPING_ID.
  
Агрегатные функции могут быть использованы в качестве выражений только в следующих случаях.
-   Список выбора инструкции SELECT (вложенный или внешний запрос).  
-   Предложение HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет следующие агрегатные функции.
  
|||  
|-|-|  
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[MIN](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[SUM](../../t-sql/functions/sum-transact-sql.md)|  
|[COUNT](../../t-sql/functions/count-transact-sql.md)|[STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[GROUPING](../../t-sql/functions/grouping-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|  
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|  
  
## <a name="see-also"></a>См. также:
[Встроенные функции (Transact-SQL)](../../t-sql/functions/functions.md)  
[ЧЕРЕЗ предложение &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
