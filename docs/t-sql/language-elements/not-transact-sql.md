---
title: "НЕ (Transact-SQL) | Документы Microsoft"
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
- NOT_TSQL
- NOT
dev_langs:
- TSQL
helpviewer_keywords:
- negating Boolean input
- NOT operator [Transact-SQL]
- expressions [SQL Server], negating
- reversing Boolean expression values
ms.assetid: dc07cc35-20f1-46e6-9995-2938390dc19a
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 85cdc60ebe0c6f66624b539e0f20d83f32c19500
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="not-transact-sql"></a>NOT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Инвертирует входное логическое значение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[ NOT ] boolean_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Любое допустимое логическое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 Оператор NOT изменяет значение любого логического выражения на противоположное.  
  
## <a name="remarks"></a>Замечания  
 Использование оператора NOT инвертирует выражение.  
  
 В следующей таблице показаны результаты сравнения значений TRUE и FALSE при использовании оператора NOT.  
  
||NOT|  
|------|---------|  
|**ЗНАЧЕНИЕ TRUE**|FALSE|  
|**ЗНАЧЕНИЕ FALSE**|TRUE|  
|**НЕИЗВЕСТНЫЙ**|UNKNOWN|  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится поиск всех велосипедов серебристого цвета по цене не выше 400 долларов США.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID, Name, Color, StandardCost  
FROM Production.Product  
WHERE ProductNumber LIKE 'BK-%' AND Color = 'Silver' AND NOT StandardCost > 400;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `ProductID   Name                     Color         StandardCost`  
  
 `---------   -------------------      ------      ------------`  
  
 `984         Mountain-500 Silver, 40  Silver        308.2179`  
  
 `985         Mountain-500 Silver, 42  Silver        308.2179`  
  
 `986         Mountain-500 Silver, 44  Silver        308.2179`  
  
 `987         Mountain-500 Silver, 48  Silver        308.2179`  
  
 `988         Mountain-500 Silver, 52  Silver        308.2179`  
  
 `(6 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример ограничивает результаты для `SalesOrderNumber` значения, начиная с `SO6` и `ProductKeys` больше или равен 400.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductKey, CustomerKey, OrderDateKey, ShipDateKey  
FROM FactInternetSales  
WHERE SalesOrderNumber LIKE 'SO6%' AND NOT ProductKey < 400;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  



