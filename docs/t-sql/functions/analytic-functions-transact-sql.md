---
description: Функции аналитики (Transact-SQL)
title: Аналитические функции (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 60fbff84-673b-48ea-9254-6ecdad20e7fe
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 00bd4984d253fe36cd498e1d6bc0e44b72fd0b1b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482104"
---
# <a name="analytic-functions-transact-sql"></a>Функции аналитики (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

SQL Server поддерживает указанные ниже аналитические функции:

- [CUME_DIST &#40; Transact-SQL &#41;](../../t-sql/functions/cume-dist-transact-sql.md)
- [FIRST_VALUE (Transact-SQL)](../../t-sql/functions/first-value-transact-sql.md)
- [LAG &#40;Transact-SQL&#41;](../../t-sql/functions/lag-transact-sql.md)
- [LAST_VALUE (Transact-SQL)](../../t-sql/functions/last-value-transact-sql.md)
- [LEAD &#40;Transact-SQL&#41;](../../t-sql/functions/lead-transact-sql.md)
- [PERCENT_RANK (Transact-SQL)](../../t-sql/functions/percent-rank-transact-sql.md)
- [PERCENTILE_CONT (Transact-SQL)](../../t-sql/functions/percentile-cont-transact-sql.md)  
- [PERCENTILE_DISC (Transact-SQL)](../../t-sql/functions/percentile-disc-transact-sql.md)
  
Аналитические функции вычисляют статистическое значение на основе группы строк. В отличие от агрегатных функций, аналитические функции могут возвращать несколько строк для каждой группы. Аналитические функции можно использовать для вычисления скользящих средних, промежуточных итогов, процентных долей или первых N результатов в группе.
 
## <a name="see-also"></a>См. также раздел

[Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)
