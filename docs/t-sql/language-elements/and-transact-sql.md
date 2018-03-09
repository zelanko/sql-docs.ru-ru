---
title: "(Transact-SQL) и | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AND_TSQL
- AND
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], TRUE
- TRUE
- AND, about AND operators
- AND
- combining expressions
ms.assetid: b61d7f8d-5a51-49b7-91dd-f6190a5a0fb9
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 340905e1f4ed4917fa4485278e43c6dc754f6164
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="and-transact-sql"></a>AND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Объединяет два логических выражения и возвращает **TRUE** Если оба выражения имеют **TRUE**. Если в инструкции используется более одного логического оператора **AND** операторы вычисляются первыми. Можно изменить порядок вычисления с помощью скобок.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
boolean_expression AND boolean_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) , возвращает значение типа Boolean: **TRUE**, **FALSE**, или **Неизвестный**.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 Возвращает значение TRUE, если оба выражения — TRUE.  
  
## <a name="remarks"></a>Remarks  
 В следующей диаграмме показаны результаты сравнения значений TRUE и FALSE с использованием оператора AND.  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**ЗНАЧЕНИЕ TRUE**|TRUE|FALSE|UNKNOWN|  
|**ЗНАЧЕНИЕ FALSE**|FALSE|FALSE|FALSE|  
|**UNKNOWN**|UNKNOWN|FALSE|UNKNOWN|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-and-operator"></a>A. Использование оператора AND  
 В следующем примере выбираются данные о сотрудниках, занимающих должность `Marketing Assistant`, начисленная продолжительность отпуска для которых составляет более `41` часов.  
  
```  
-- Uses AdventureWorks  
  
SELECT  BusinessEntityID, LoginID, JobTitle, VacationHours   
FROM HumanResources.Employee  
WHERE JobTitle = 'Marketing Assistant'  
AND VacationHours > 41 ;  
```  
  
### <a name="b-using-the-and-operator-in-an-if-statement"></a>Б. Использование оператора AND в инструкции IF  
 В следующих примерах демонстрируется использование оператора AND в инструкции IF. В первой инструкции условия `1 = 1` и `2 = 2` имеют значение true, отсюда итоговый результат true. Во втором примере, аргумент `2 = 17` имеет значение false, поэтому результат имеет значение false.  
  
```  
IF 1 = 1 AND 2 = 2  
BEGIN  
   PRINT 'First Example is TRUE'  
END  
ELSE PRINT 'First Example is FALSE';  
GO  
  
IF 1 = 1 AND 2 = 17  
BEGIN  
   PRINT 'Second Example is TRUE'  
END  
ELSE PRINT 'Second Example is FALSE' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
