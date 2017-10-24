---
title: "Выражения (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Boolean expressions
- expressions [SQL Server], about expressions
- combining expressions
- Transact-SQL expressions
- expressions [SQL Server], combining
- simple expressions [SQL Server]
- complex expressions [SQL Server]
ms.assetid: ee53c5c8-e36c-40f9-8cd1-d933791b98fa
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 826d1ab9f4a0a68d692551ae58a529ab8b7ebfae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="expressions-transact-sql"></a>Выражения (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Сочетание символов и операторов, используемое компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] для вычисления одиночного значения данных. Отдельные константы, переменные, столбцы и скалярные функции являются примерами простых выражений. Для соединения двух и более простых выражений в одно сложное можно использовать операторы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
{ constant | scalar_function | [ table_name. ] column | variable   
    | ( expression ) | ( scalar_subquery )   
    | { unary_operator } expression   
    | expression { binary_operator } expression   
    | ranking_windowed_function | aggregate_windowed_function  
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Expression in a SELECT statement  
<expression> ::=   
{  
    constant   
    | scalar_function   
    | column  
    | variable  
    | ( expression  )  
    | { unary_operator } expression   
    | expression { binary_operator } expression   
}  
[ COLLATE Windows_collation_name ]  
  
-- Scalar Expression in a DECLARE, SET, IF…ELSE, or WHILE statement  
<scalar_expression> ::=  
{  
    constant   
    | scalar_function   
    | variable  
    | ( expression  )  
    | (scalar_subquery )  
    | { unary_operator } expression   
    | expression { binary_operator } expression   
}  
[ COLLATE { Windows_collation_name ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|----------|----------------|  
|*Константа*|Символ, представляющий одно конкретное значение данных. Дополнительные сведения см. в разделе [константы &#40; Transact-SQL &#41; ](../../t-sql/data-types/constants-transact-sql.md).|  
|*scalar_function*|— Это единица [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, который предоставляет определенную службу и возвращает одиночное значение. *scalar_function* может быть встроенной скалярной функцией, таких как SUM, GETDATE или CAST или скалярные определяемые пользователем функции.|  
|[ *table_name***.** ]|Имя или псевдоним таблицы.|  
|*столбец*|Имя столбца. Только имя столбца используется в выражении.|  
|*переменная*|Имя переменной или параметр. Дополнительные сведения см. в статье [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md).|  
|**(** *выражение***)** |Любое допустимое выражение из определенных в этом разделе. Скобки являются операторами группировки, гарантирующими, что все операторы выражения внутри скобок будут выполнены, прежде чем результирующее выражение будет объединено с другим.|  
|**(** *scalar_subquery* **)**|Вложенный запрос, возвращающий одиночное значение. Например:<br /><br /> `SELECT MAX(UnitPrice)`<br /><br /> `FROM Products`|  
|{ *unary_operator* }|Унарные операторы можно применять только к выражениям, выполняемым с любыми типами данных из категории числовых типов данных. Оператор, имеющий только один числовой операнд:<br /><br /> + обозначает положительное число.<br /><br /> - обозначает отрицательное число.<br /><br /> ~ обозначает оператор дополнения.|  
|{ *binary_operator* }|Этот оператор указывает, как объединяются два выражения для получения единого результата. *binary_operator* может быть арифметический оператор, оператор присваивания (=), побитовый оператор, оператор сравнения, логический оператор, оператор объединения строк (+) или унарный оператор. Дополнительные сведения об операторах см. в разделе [операторами &#40; Transact-SQL &#41; ](../../t-sql/language-elements/operators-transact-sql.md).|  
|*ranking_windowed_function*|Любая ранжирующая функция языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения см. в разделе [Ранжирующие функции &#40; Transact-SQL &#41; ](../../t-sql/functions/ranking-functions-transact-sql.md).|  
|*aggregate_windowed_function*|Любая агрегатная функция языка [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащая предложение OVER. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).|  
  
## <a name="expression-results"></a>Результаты выражения  
 Для простых выражений, состоящих из одной константы, переменной, скалярной функции или имени столбца, в качестве типа данных, параметров сортировки, числа разрядов, точности и значения выражения используются тип данных, параметры сортировки, число разрядов, точность и значение элемента, на который они ссылаются.  
  
 При объединении двух выражений с помощью сравнения или логических операторов, тип данных результата: логическое значение, а значение является одним из следующих: TRUE, FALSE или UNKNOWN. Дополнительные сведения о логических типах данных см. в разделе [операторы сравнения &#40; Transact-SQL &#41; ](../../t-sql/language-elements/comparison-operators-transact-sql.md).  
  
 При объединении двух выражений с помощью арифметических, побитовых или строковых операторов тип данных результата определяется используемым оператором.  
  
 Сложные выражения, составленные из нескольких символов и операторов, вычисляются в одиночные результаты. Тип данных, параметры сортировки, точность и значение результирующего выражения определяются объединением составляющих выражений (по два за один раз) до тех пор, пока не будет получен конечный результат. Последовательность, в которой эти выражения объединяются, зависит от приоритета операторов в выражении.  
  
## <a name="remarks"></a>Замечания  
 Два выражения можно объединить каким-либо оператором, если оба они относятся к типам данных, поддерживаемым оператором, и выполняется хотя бы одно из следующих условий.  
  
-   Выражения относятся к одному типу данных.  
  
-   Тип данных с более низким приоритетом может быть неявно преобразован в тип данных с более высоким приоритетом.  
  
 Если выражения не удовлетворяют этим условиям, функция CAST или CONVERT явным образом преобразует тип данных с более низким приоритетом или в тип данных с более высоким приоритетом, или в промежуточный тип данных, который затем может быть неявно преобразован в тип данных с более высоким приоритетом.  
  
 Если неявное или явное преобразование не поддерживается, эти два выражения объединить невозможно.  
  
 Параметры сортировки любого выражения, результатом которого является символьная строка, определяются правилами очередности параметров сортировки. Дополнительные сведения см. в разделе [очередность параметров сортировки &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).  
  
 В языке программирования, таких как C или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], результатом вычисления выражения всегда один результат. Выражения в [!INCLUDE[tsql](../../includes/tsql-md.md)] выберите список подчиняются правилу: выражение вычисляется по отдельности для каждой строки в результирующем наборе. У отдельных выражений могут быть различные значения в каждой строке результирующего набора, но у каждой строки имеется только одно значение для выражения. Например, в следующей инструкции `SELECT` выражениями являются как ссылка на `ProductID`, так и значение `1+2` в списке выбора:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, 1+2  
FROM Production.Product;  
GO  
```  
  
 Выражение `1+2` дает результат `3` в каждой строке результирующего набора. Несмотря на то, что выражение `ProductID` формирует уникальное значение для каждой строки в результирующем наборе, в каждой строке содержится только одно значение для `ProductID`.  
  
## <a name="see-also"></a>См. также:  
 [В ЧАСОВОМ ПОЯСЕ &#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [ОБЪЕДИНЕННЫЙ &#40; Transact-SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)   
 [Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Приоритет типов данных &#40; Transact-SQL &#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Функция NULLIF &#40; Transact-SQL &#41;](../../t-sql/language-elements/nullif-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

