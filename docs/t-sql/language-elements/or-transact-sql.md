---
title: "ИЛИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OR_TSQL
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], combining
- combining conditions
- OR operator
ms.assetid: b730a256-4a63-4880-9906-65b05cd9caf2
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 590410dd84275f63bc610ac436410c7d323eb8e3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="or-transact-sql"></a>OR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Объединяет два условия. Если в инструкции используется более одного логического оператора, то операторы OR вычисляются после операторов AND. Однако порядок выполнения можно изменить с помощью скобок.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
boolean_expression OR boolean_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) , возвращающий значение TRUE, FALSE или UNKNOWN.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 Оператор OR возвращает значение TRUE, если любое из условий равно значению TRUE.  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице показан результат выполнения оператора OR.  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**ЗНАЧЕНИЕ TRUE**|TRUE|TRUE|TRUE|  
|**ЗНАЧЕНИЕ FALSE**|TRUE|FALSE|UNKNOWN|  
|**НЕИЗВЕСТНЫЙ**|TRUE|UNKNOWN|UNKNOWN|  
  
## <a name="examples"></a>Примеры  
 В следующем примере представление `vEmployeeDepartmentHistory` используется для извлечения имен персонала `Quality Assurance`, работающего либо в вечернюю, либо в ночную смену. Если скобки не указаны, запрос возвращает сотрудников фирмы `Quality Assurance`, работающих в вечернюю смену, и всех сотрудников, работающих в ночную смену.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Shift   
FROM HumanResources.vEmployeeDepartmentHistory  
WHERE Department = 'Quality Assurance'  
   AND (Shift = 'Evening' OR Shift = 'Night');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 FirstName    LastName         Shift 
 ------------ ---------------- ------- 
 Andreas      Berglund         Evening 
 Sootha       Charncherngkha   Night
 ```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере извлекаются имена сотрудников, которые либо заработать `BaseRate` меньше 20 или иметь `HireDate` 1 января 2001 года или более поздней версии.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, BaseRate, HireDate   
FROM DimEmployee  
WHERE BaseRate < 10 OR HireDate >= '2001-01-01';  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  



