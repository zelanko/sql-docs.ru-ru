---
title: CEILING (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CEILING_TSQL
- CEILING
dev_langs:
- TSQL
helpviewer_keywords:
- smallest integer great than or equal to expression
- integers [SQL Server]
- CEILING function [Transact-SQL]
ms.assetid: e736b43a-9457-4781-95a4-4bcf9d4fc46a
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 83f9735ca8a40997e88430810cf4119c060f0c36
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844492"
---
# <a name="ceiling-transact-sql"></a>CEILING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает наименьшее целое, большее или равное указанному числовому выражению.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CEILING ( numeric_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*numeric_expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) категории точного числового или приблизительного числового типа данных. Для этой функции тип данных **bit** недопустим.
  
## <a name="return-types"></a>Типы возвращаемых данных
Возвращаемые значения имеют тот же тип, что и аргумент *numeric_expression*.
  
## <a name="examples"></a>Примеры  
В этом примере показано применение функции CEILING с положительными числовыми, отрицательными числовыми и нулевыми входными значениями.
  
```sql
SELECT CEILING($123.45), CEILING($-123.45), CEILING($0.0);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
--------- --------- -------------------------   
124.00    -123.00    0.00                       
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)
  
  
