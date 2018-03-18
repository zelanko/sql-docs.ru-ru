---
title: "% (остаток от деления) (Transact-SQL) | Документы Майкрософт"
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
- modulo
- modulus
- '% (Modulo)'
- '% (Modulus)'
- MOD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- '% (modulo operator)'
- '% (modulus operator)'
- remainder of division operation
- modulo operator (%)
- modulus operator (%)
ms.assetid: f93c662e-f405-486e-bf23-a2d03907b5bd
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 927b993e2b93ef670633ae1594c86178662ebabb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="-modulus-transact-sql"></a>% (остаток от деления) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает остаток от деления одного числа на другое.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Аргументы  
 *dividend*  
 Делимое числовое выражение. Аргумент *dividend* должен быть допустимым [выражением](../../t-sql/language-elements/expressions-transact-sql.md) любого типа из категорий целочисленных или денежных типов данных или типа **numeric**.  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. Аргумент *divisor* должен быть допустимым выражением любого типа из категорий целочисленных или денежных типов данных или типа **numeric**.  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов.  
  
## <a name="remarks"></a>Remarks  
 Оператор взятия остатка от деления можно использовать в списке выбора инструкции SELECT с любым сочетанием имен столбцов, числовых констант или любым допустимым выражением из категории целочисленных или денежных типов, а также типа **numeric**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example"></a>A. Простой пример  
 В следующем примере выполняется деление числа 38 на 5. Это приводит к получению числа 7, являющегося целой частью результата, и показывает, что в качестве остатка от деления возвращается число 3.  
  
```  
SELECT 38 / 5 AS Integer, 38 % 5 AS Remainder ;  
  
```  
  
### <a name="b-example-using-columns-in-a-table"></a>Б. Пример с использованием столбцов в таблице  
 Следующий пример возвращает код продукта, цену единицы модуля продукта и остаток от деления цены каждого продукта, преобразовывает к целому значению, в количество заказанных продуктов.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(100)ProductID, UnitPrice, OrderQty,  
   CAST((UnitPrice) AS int) % OrderQty AS Modulo  
FROM Sales.SalesOrderDetail;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example"></a>В. Простой пример  
 В приведенном ниже примере показаны результаты применения оператора `%` при делении 3 на 2.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) 3%2 FROM dimEmployee;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
1         
```  
  
## <a name="see-also"></a>См. также:  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [%= (присваивание остатка от деления) (Transact-SQL)](../../t-sql/language-elements/modulo-equals-transact-sql.md)   
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


