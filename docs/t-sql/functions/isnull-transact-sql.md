---
title: "ISNULL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISNULL
- ISNULL_TSQL
- IFNULL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- replacing null values
- null values [SQL Server], ISNULL
- null values [SQL Server], replacement values
- ISNULL function
ms.assetid: 6f3e5802-864b-4e77-9862-657bb5430b68
caps.latest.revision: "42"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ad067dd6df83e49c3a46fd5955945f79c20d1b96
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="isnull-transact-sql"></a>Функция ISNULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Заменяет значение NULL указанным замещающим значением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ISNULL ( check_expression , replacement_value )  
```  
  
## <a name="arguments"></a>Аргументы  
 *check_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) для проверки NULL. *check_expression* может быть любого типа.  
  
 *replacement_value*  
 Выражение, которое должно быть возвращено, если *check_expression* имеет значение NULL. *replacement_value* должен иметь тип, который неявно преобразуется в тип *check_expresssion*.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает тот же тип как *check_expression*. Если литерал NULL указывается как *check_expression*, возвращает тип данных *replacement_value*. Если литерал NULL указывается как *check_expression* и не *replacement_value* предоставлен, возвращает **int**.  
  
## <a name="remarks"></a>Замечания  
 Значение *check_expression* возвращается, если она не NULL, в противном случае — *replacement_value* возвращается после неявно преобразуется в тип *check_expression*, если типы различны. *replacement_value* может быть усечена, если *replacement_value* длиннее, чем *check_expression*.  
  
> [!NOTE]  
>  Используйте [COALESCE &#40; Transact-SQL &#41; ](../../t-sql/language-elements/coalesce-transact-sql.md) для возврата первое значение отличное от null.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-isnull-with-avg"></a>A. Использование функции ISNULL с функцией AVG  
 Следующий пример демонстрирует расчет среднего значения веса всех продуктов. Все записи со значением NULL в столбце `50` таблицы `Weight` заменяются значением `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT AVG(ISNULL(Weight, 50))  
FROM Production.Product;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 -------------------------- 
59.79  
  
 (1 row(s) affected)
 ```  
  
### <a name="b-using-isnull"></a>Б. Использование функции ISNULL  
 Следующий пример производит выборку описания, процента скидки, минимального и максимального количества для всех специальных предложений из базы `AdventureWorks2012`. Если максимальное количество для отдельного специального предложения равно NULL, отображаемое значение `MaxQty` в результирующем наборе заменяется на `0.00`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Description, DiscountPct, MinQty, ISNULL(MaxQty, 0.00) AS 'Max Quantity'  
FROM Sales.SpecialOffer;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|  Description       |  DiscountPct    |   MinQty    |   Максимальное количество       |
|  ---------------   |  -------------  |   --------  |   ---------------    |
|  Без скидки       |  0,00           |   0         |   0                  |
|  Оптовая скидка   |  0.02           |   11        |   14                 |
|  Оптовая скидка   |  0,05           |   15        |   4                  |
|  Оптовая скидка   |  0.10           |   25        |   0                  |
|  Оптовая скидка   |  0,15           |   41        |   0                  |
|  Оптовая скидка   |  0.20           |   61        |   0                  |
|  Mountain-100 Cl   |  0.35           |   0         |   0                  |
|  Спорт Helmet Di   |  0.10           |   0         |   0                  |
|  Road-650 Overst   |  0.30           |   0         |   0                  |
|  Mountain Tire S   |  0,50           |   0         |   0                  |
|  Спорт Helmet Di   |  0,15           |   0         |   0                  |
|  LL Road Frame S   |  0.35           |   0         |   0                  |
|  Обр Touring-3000   |  0,15           |   0         |   0                  |
|  Touring-1000 Pr   |  0.20           |   0         |   0                  |
|  Half-Price Peda   |  0,50           |   0         |   0                  |
|  Mountain-500 Si   |  0.40           |   0         |   0                  |

 `(16 row(s) affected)`  
  
### <a name="c-testing-for-null-in-a-where-clause"></a>В. Проверка значений NULL в предложении WHERE  
 Не используйте для поиска значений NULL выражение ISNULL, вместо него следует использовать выражение IS NULL. В следующем примере выполняется поиск всех продуктов, имеющих значение `NULL` в столбце веса. Заметьте, что между словами `IS` и `NULL` стоит пробел.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight  
FROM Production.Product  
WHERE Weight IS NULL;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-isnull-with-avg"></a>Г. Использование функции ISNULL с функцией AVG  
 В следующем примере вычисляется среднее значение веса всех продуктов в образец таблицы. Все записи со значением NULL в столбце `50` таблицы `Weight` заменяются значением `Product`.  
  
```  
-- Uses AdventureWorks  
  
SELECT AVG(ISNULL(Weight, 50))  
FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------------------------   
52.88   
```  
  
### <a name="e-using-isnull"></a>Д. Использование функции ISNULL  
 В следующем примере используется функция ISNULL для проверки наличия значений NULL в столбце `MinPaymentAmount` и отобразить значение `0.00` для этих строк.  
  
```  
-- Uses AdventureWorks  
  
SELECT ResellerName,   
       ISNULL(MinPaymentAmount,0) AS MinimumPayment  
FROM dbo.DimReseller  
ORDER BY ResellerName;  
  
```  
  
 Здесь приводится частичный результирующий набор.  
  
|  ResellerName                |  MinimumPayment    |
|  -------------------------   |  --------------    |
|  Ассоциация велосипеда       |     0.0000         |
|  Bike Store                |     0.0000         |
|  Производственного цикла                |     0.0000         |
|  Компания велосипед нормально     |     0.0000         |
|  Это типичный велосипеда магазин         |   200.0000         |
|  Допустимые продажи и службы  |     0.0000         |
  
### <a name="f-using-is-null-to-test-for-null-in-a-where-clause"></a>Е. Использование IS NULL для проверки на значения NULL в предложении WHERE  
 Следующий пример находит все продукты, которые имеют `NULL` в `Weight` столбца. Заметьте, что между словами `IS` и `NULL` стоит пробел.  
  
```  
-- Uses AdventureWorks  
  
SELECT EnglishProductName, Weight  
FROM dbo.DimProduct  
WHERE Weight IS NULL;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [РАВЕН NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [ОБЪЕДИНЕННЫЙ &#40; Transact-SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  

