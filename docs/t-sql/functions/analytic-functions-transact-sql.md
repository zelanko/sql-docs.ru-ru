---
title: Аналитические функции (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 60fbff84-673b-48ea-9254-6ecdad20e7fe
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a850e153a2c64fb3de4828d2698d16cad97d7d17
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38023322"
---
# <a name="analytic-functions-transact-sql"></a>Функции аналитики (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

SQL Server поддерживает указанные ниже аналитические функции:
  
|||  
|-|-|  
|[CUME_DIST &#40; Transact-SQL &#41;](../../t-sql/functions/cume-dist-transact-sql.md)|[LEAD &#40; Transact-SQL &#41;](../../t-sql/functions/lead-transact-sql.md)|  
|[FIRST_VALUE (Transact-SQL)](../../t-sql/functions/first-value-transact-sql.md)|[PERCENTILE_CONT (Transact-SQL)](../../t-sql/functions/percentile-cont-transact-sql.md)|  
|[LAG &#40;Transact-SQL&#41;](../../t-sql/functions/lag-transact-sql.md)|[PERCENTILE_DISC (Transact-SQL)](../../t-sql/functions/percentile-disc-transact-sql.md)|  
|[LAST_VALUE (Transact-SQL)](../../t-sql/functions/last-value-transact-sql.md)|[PERCENT_RANK (Transact-SQL)](../../t-sql/functions/percent-rank-transact-sql.md)|  
  
Аналитические функции вычисляют статистическое значение на основе группы строк. В отличие от агрегатных функций, аналитические функции могут возвращать несколько строк для каждой группы. Аналитические функции можно использовать для вычисления скользящих средних, промежуточных итогов, процентных долей или первых N результатов в группе.
 
## <a name="see-also"></a>См. также раздел
[Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
