---
title: IIF (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IIF_TSQL
- IIF
dev_langs:
- TSQL
helpviewer_keywords:
- IIF function
ms.assetid: e3ccf8ed-1cec-43ac-90b7-d8597c24b050
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4234d8df62c024e68a83497c763253044011b5b8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38022788"
---
# <a name="logical-functions---iif-transact-sql"></a>Логические функции — IIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает одно из двух значений в зависимости от того, принимает логическое выражение значение true или false.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IIF ( boolean_expression, true_value, false_value )  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Допустимое логическое выражение.  
  
 Если этот аргумент не является логическим выражением, то возникает ошибка синтаксиса.  
  
 *true_value*  
 Возвращаемое значение, если *boolean_expression* имеет значение true.  
  
 *false_value*  
 Возвращаемое значение, если *boolean_expression* имеет значение false.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает тип данных с наивысшим приоритетом из типов, имеющихся в *true_value* и *false_value*. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 IIF является быстрым способом написания выражения CASE. Оно вычисляет логическое выражение, переданное в качестве первого аргумента, а затем, исходя из результата вычисления, возвращает один из двух других аргументов. Другими словами, если логическое выражение имеет значение true, то возвращается *true_value*, если же логическое выражение имеет значение false или неизвестно, то возвращается *false_value*. *true_value* и *false_value* могут быть любого типа. Эти же правила применяются к выражению CASE для логических выражений, обработки значения NULL, а возвращаемые типы также применяются к IIF. Дополнительные сведения см. в статье [CASE (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md).  
  
 Тот факт, что IIF переводится в CASE, также оказывает влияние на другие аспекты работы этой функции. Поскольку выражения CASE могут быть вложенными только до уровня 10, инструкции IIF также могут быть вложенными максимум до уровня 10. Кроме того, выполнение IIF переносится на другие серверы как семантически равное выражение CASE, при этом для нее характерно все поведение выполняемого удаленно выражения CASE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-iif-example"></a>A. Пример простой инструкции IIF  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
TRUE  
  
(1 row(s) affected)  
```  
  
### <a name="b-iif-with-null-constants"></a>Б. Инструкция IIF с константами NULL  
  
```  
SELECT IIF ( 45 > 30, NULL, NULL ) AS Result;  
```  
  
 Результатом выполнения этой инструкции будет ошибка.  
  
### <a name="c-iif-with-null-parameters"></a>В. Инструкция IIF с параметрами NULL  
  
```  
DECLARE @P INT = NULL, @S INT = NULL;  
SELECT IIF ( 45 > 30, @p, @s ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
NULL  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [CASE (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md)   
 [CHOOSE (Transact-SQL)](../../t-sql/functions/logical-functions-choose-transact-sql.md)  
  
  
