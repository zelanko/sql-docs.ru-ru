---
title: WHILE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WHILE_TSQL
- WHILE
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], repeated executions
- statement blocks [SQL Server]
- repeated statement executions
- nested WHILE loops
- WHILE keyword
ms.assetid: 52dd29ab-25d7-4fd3-a960-ac55c30c9ea9
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2c60dd1be8f409c1338e7fe6a4c0548fbcf05e6
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635369"
---
# <a name="while-transact-sql"></a>WHILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]


  Ставит условие повторного выполнения SQL-инструкции или блока инструкций. Эти инструкции вызываются в цикле, пока указанное условие истинно. Вызовами инструкций в цикле WHILE можно контролировать из цикла с помощью ключевых слов BREAK и CONTINUE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
-- Syntax for SQL Server and Azure SQL Database  
  
WHILE Boolean_expression   
     { sql_statement | statement_block | BREAK | CONTINUE }  
  
```  
  
```syntaxsql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
WHILE Boolean_expression   
     { sql_statement | statement_block | BREAK }  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Boolean_expression*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md), возвращающее значение **TRUE** или **FALSE**. Если логическое выражение содержит инструкцию SELECT, инструкция SELECT должна быть заключена в скобки.  
  
 {*sql_statement* | *statement_block*}  
 Любая инструкция или группа инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], определенная в виде блока инструкций. Для определения блока инструкций используйте ключевые слова потока управления BEGIN и END.  
  
 BREAK  
 Приводит к выходу из ближайшего цикла WHILE. Вызываются инструкции, следующие за ключевым словом END, обозначающим конец цикла.  
  
 CONTINUE  
 Выполняет цикл WHILE для перезагрузки, не учитывая все инструкции, следующие после ключевого слова CONTINUE.  
  
## <a name="remarks"></a>Remarks  
 Если вложенными являются два цикла WHILE или более, внутренний оператор BREAK существует до следующего внешнего цикла. Все инструкции после окончания внутреннего цикла выполняются в первую очередь, а затем перезапускается следующий внешний цикл.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-break-and-continue-with-nested-ifelse-and-while"></a>A. Использование ключевых слов BREAK и CONTINUE внутри вложенных конструкций IF...ELSE и WHILE  
 В следующем примере в случае, если средняя цена продуктов из списка меньше чем `$300`, цикл `WHILE` удваивает цены, а затем выбирает максимальную. В том случае, если максимальная цена меньше или равна `$500`, цикл `WHILE` повторяется и снова удваивает цены. Этот цикл продолжает удваивать цены до тех пор, пока максимальная цена не будет больше чем `$500`, затем выполнение цикла `WHILE` прекращается, о чем выводится соответствующее сообщение.  
  
```  
USE AdventureWorks2012;  
GO  
WHILE (SELECT AVG(ListPrice) FROM Production.Product) < $300  
BEGIN  
   UPDATE Production.Product  
      SET ListPrice = ListPrice * 2  
   SELECT MAX(ListPrice) FROM Production.Product  
   IF (SELECT MAX(ListPrice) FROM Production.Product) > $500  
      BREAK  
   ELSE  
      CONTINUE  
END  
PRINT 'Too much for the market to bear';  
```  
  
### <a name="b-using-while-in-a-cursor"></a>Б. Применение инструкции WHILE в курсоре  
 В следующем примере используется переменная `@@FETCH_STATUS` для управления действиями курсора в цикле `WHILE`.  
  
```  
DECLARE @EmployeeID as nvarchar(256)
DECLARE @Title as nvarchar(50)

DECLARE Employee_Cursor CURSOR FOR  
SELECT LoginID, JobTitle   
FROM AdventureWorks2012.HumanResources.Employee  
WHERE JobTitle = 'Marketing Specialist';  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor INTO @EmployeeID, @Title;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      Print '   ' + @EmployeeID + '      '+  @Title 
      FETCH NEXT FROM Employee_Cursor INTO @EmployeeID, @Title;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO 
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-while-loop"></a>В. Простой цикл While  
 В следующем примере в случае, если средняя цена продуктов из списка меньше чем `$300`, цикл `WHILE` удваивает цены, а затем выбирает максимальную. В том случае, если максимальная цена меньше или равна `$500`, цикл `WHILE` повторяется и снова удваивает цены. Этот цикл продолжает удваивать цены до тех пор, пока максимальная цена не будет больше, чем `$500`, после чего выполнение цикла `WHILE` прекращается.  
  
```  
-- Uses AdventureWorks  
  
WHILE ( SELECT AVG(ListPrice) FROM dbo.DimProduct) < $300  
BEGIN  
    UPDATE dbo.DimProduct  
        SET ListPrice = ListPrice * 2;  
    SELECT MAX ( ListPrice) FROM dbo.DimProduct  
    IF ( SELECT MAX (ListPrice) FROM dbo.DimProduct) > $500  
        BREAK;  
END  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Язык управления потоком (Transact-SQL)](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Курсоры (Transact-SQL)](../../t-sql/language-elements/cursors-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  


