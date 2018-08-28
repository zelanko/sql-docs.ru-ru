---
title: Арифметические операторы (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], arithmetic
- arithmetic operators
- math operations [Transact-SQL]
ms.assetid: a41b92a5-1061-4e4d-bb3b-a180b73c88fa
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ca21840e43eeffeaf1608d3ccab8794e18ff3a2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43057827"
---
# <a name="arithmetic-operators-transact-sql"></a>Арифметические операторы (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Арифметические операторы выполняют математические операции над двумя выражениями одного или различных типов данных из категории числовых типов данных. Дополнительные сведения о категориях типов данных см. в статье [Соглашения о синтаксисе в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Оператор|Значение|  
|--------------|-------------|  
|[+ (сложение)](../../t-sql/language-elements/add-transact-sql.md)|Сложение|  
|[- (вычитание)](../../t-sql/language-elements/subtract-transact-sql.md)|Вычитание|  
|[* (умножение)](../../t-sql/language-elements/multiply-transact-sql.md)|Умножение|  
|[/ (деление)](../../t-sql/language-elements/divide-transact-sql.md)|Деление|  
|[% (остаток от деления)](../../t-sql/language-elements/modulo-transact-sql.md)|Возвращает целочисленный остаток при делении. Например, 12 % 5 = 2, поскольку остаток от деления 12 на 5 равен 2.|  
  
 Операторы (+) и (–) можно также использовать для выполнения арифметических операций со значениями типов **datetime** и **smalldatetime**.  
  
 Дополнительные сведения о точности и масштабе результатов арифметических операций см. в статье [Точность, масштаб и длина (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Математические функции (Transact-SQL)](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
