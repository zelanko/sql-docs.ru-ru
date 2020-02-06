---
title: '*= (присваивание умножения) (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '*=_TSQL'
- '*='
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, *=
- assignment operators, *=
- augmented operators, *=
- '*= (multiply equals)'
- '*= (multiplication assignment)'
ms.assetid: 816ff5dc-9a40-4c07-8351-39c194dbc079
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6ad2f4cd1c650831415eb4fea8182eaf5fb81fe
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68122091"
---
# <a name="-multiplication-assignment-transact-sql"></a>*= (присваивание умножения) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Умножает два числа и присваивает значению результат этой операции. Например, если переменная @x равна 35, то @x *= 2 принимает исходное значение @x, умножает его на 2 и присваивает переменной @x новое значение (70).  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression *= expression  
```  
  
## <a name="arguments"></a>Аргументы  
_expression_  
Любой допустимый тип данных [expression](../../t-sql/language-elements/expressions-transact-sql.md), кроме типа **bit**, в числовой категории.  
  
## <a name="result-types"></a>Типы результата  
Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
Дополнительные сведения см. в статье [&#42; (умножение) (Transact-SQL)](../../t-sql/language-elements/multiply-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
[Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)   
[Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
[Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
