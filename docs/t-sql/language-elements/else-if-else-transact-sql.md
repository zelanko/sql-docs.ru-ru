---
title: ELSE (IF...ELSE) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ELSE
- ELSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 6f2b4278-0dea-4603-bbd3-7cbad602a645
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 0fb217765b378e60a7272a46f224559516242818
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39455878"
---
# <a name="else-ifelse-transact-sql"></a>ELSE (IF...ELSE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает условия для выполнения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] (*sql_statement*), следующая за выражением *Boolean_expression*, выполняется, если выражение *Boolean_expression* имеет значение TRUE. Необязательное ключевое слово ELSE позволяет указать альтернативную инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], выполняемую в случае, если значение выражения *Boolean_expression* равно FALSE или NULL.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *Boolean_expression*  
 Выражение, возвращающее значение TRUE или FALSE. Если логическое выражение *Boolean_expression* содержит инструкцию SELECT, инструкция SELECT должна быть заключена в скобки.  
  
 { *sql_statement* | *statement_block* }  
 Любая допустимая инструкция или группа инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], определенных блоком инструкций. Чтобы определить блок инструкций (пакет), используются ключевые слова BEGIN и END языка управления выполнением. Хотя все инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] допустимы в пределах блока BEGIN...END, некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] не следует группировать вместе в пределах одного пакета (блока инструкций).  
  
## <a name="result-types"></a>Типы результата  
 **Boolean**  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-simple-boolean-expression"></a>A. Использование простого логического выражения  
 В следующем примере простое логическое выражение (`1=1`) имеет значение true, поэтому печатается первая инструкция.  
  
```  
IF 1 = 1 PRINT 'Boolean_expression is true.'  
ELSE PRINT 'Boolean_expression is false.' ;  
```  
  
 В следующем примере простое логическое выражение (`1=2`) имеет значение false, поэтому печатается вторая инструкция.  
  
```  
IF 1 = 2 PRINT 'Boolean_expression is true.'  
ELSE PRINT 'Boolean_expression is false.' ;  
GO  
```  
  
### <a name="b-using-a-query-as-part-of-a-boolean-expression"></a>Б. Использование запроса как части логического выражения  
 В следующем примере выполняется запрос как часть логического выражения. В таблице `Product` имеются данные о 10 велосипедах, которые соответствуют предложению `WHERE`, поэтому выполняется первый оператор вывода. Измените `> 5` на `> 15`, чтобы посмотреть, как может быть выполнена вторая часть инструкции.  
  
```  
USE AdventureWorks2012;  
GO  
IF   
(SELECT COUNT(*) FROM Production.Product WHERE Name LIKE 'Touring-3000%' ) > 5  
PRINT 'There are more than 5 Touring-3000 bicycles.'  
ELSE PRINT 'There are 5 or less Touring-3000 bicycles.' ;  
GO  
```  
  
### <a name="c-using-a-statement-block"></a>В. Использование блока инструкций  
 В следующем примере запрос выполняется как часть логического выражения, а затем выполняются немного отличающиеся блоки инструкций, основанные на результате логического выражения. Каждый блок инструкций начинается с `BEGIN` и завершается `END`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @AvgWeight decimal(8,2), @BikeCount int  
IF   
(SELECT COUNT(*) FROM Production.Product WHERE Name LIKE 'Touring-3000%' ) > 5  
BEGIN  
   SET @BikeCount =   
        (SELECT COUNT(*)   
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%');  
   SET @AvgWeight =   
        (SELECT AVG(Weight)   
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%');  
   PRINT 'There are ' + CAST(@BikeCount AS varchar(3)) + ' Touring-3000 bikes.'  
   PRINT 'The average weight of the top 5 Touring-3000 bikes is ' + CAST(@AvgWeight AS varchar(8)) + '.';  
END  
ELSE   
BEGIN  
SET @AvgWeight =   
        (SELECT AVG(Weight)  
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%' );  
   PRINT 'Average weight of the Touring-3000 bikes is ' + CAST(@AvgWeight AS varchar(8)) + '.' ;  
END ;  
GO  
```  
  
### <a name="d-using-nested-ifelse-statements"></a>Г. Использованием вложенных инструкций IF...ELSE  
 Следующий пример иллюстрирует порядок вставки одной инструкции IF…ELSE в другую. Задайте значения переменной `@Number` равными `5`, `50` и `500`, чтобы проверить каждую инструкцию.  
  
```  
DECLARE @Number int;  
SET @Number = 50;  
IF @Number > 100  
   PRINT 'The number is large.';  
ELSE   
   BEGIN  
      IF @Number < 10  
      PRINT 'The number is small.';  
   ELSE  
      PRINT 'The number is medium.';  
   END ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-query-as-part-of-a-boolean-expression"></a>Д. Использование запроса как части логического выражения  
 В следующем примере используется `IF…ELSE` для определения того, какой из двух ответов показать пользователю, на основе веса элемента в таблице `DimProduct`.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct WHERE ProductKey=@productKey)   
    (SELECT @productKey, EnglishDescription, Weight, 'This product is too heavy to ship and is only available for pickup.' FROM DimProduct WHERE ProductKey=@productKey)  
ELSE  
    (SELECT @productKey, EnglishDescription, Weight, 'This product is available for shipping or pickup.' FROM DimProduct WHERE ProductKey=@productKey)  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Язык управления потоком (Transact-SQL)](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  
  
  


