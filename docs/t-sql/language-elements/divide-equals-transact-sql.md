---
description: /= (Присваивание деления) (Transact-SQL)
title: (Присваивание деления) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- /=_TSQL
- /=
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, /=
- assignment operators, /=
- augmented operators, /=
- /= (divide equals)
ms.assetid: 9ab25d1e-5c98-4dd7-b2cd-9f49499c86e7
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bded455f287aca7fd4f4b66491c931b618c7f93c
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96128259"
---
# <a name="-division-assignment-transact-sql"></a>/= (Присваивание деления) (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Одно число делится на другое, и значение задается для результата операции. Например, если переменная @x равна 34, то `@x /= 2` принимает исходное значение @x, делит его на 2 и задает переменной @x новое значение (17).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql  
expression /= expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *expression*  
 Любое допустимое выражение [expression](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных числовой категории, кроме типа данных **bit**.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Комментарии  
 Дополнительные сведения см. в разделе [(Деление) (Transact-SQL)](../../t-sql/language-elements/divide-transact-sql.md).  

## <a name="examples"></a>Примеры  
В следующем примере переменной присваивается значение 17. Затем используется оператор `/=` для присвоения переменной половины исходного значения.  
```sql  
DECLARE @myVariable DECIMAL(5,2);
SET @myVariable = 17.5;
SET @myVariable /= 2;
SELECT @myVariable AS ResultVariable;  
```
  
[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]  

|ResultVariable | 
|--- |
|8,75 |

## <a name="see-also"></a>См. также  
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
