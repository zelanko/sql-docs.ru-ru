---
title: "ВЫБЕРИТЕ @local_variable (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- variable_TSQL
- '@loca_variable'
- '@local'
- variable
- '@loca_variable_TSQL'
- '@local_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- variables [SQL Server], assigning
- SELECT statement [SQL Server], @local_variable
- '@local_variable'
- local variables [SQL Server]
ms.assetid: 8e1a9387-2c5d-4e51-a1fd-a2a95f026d6f
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: c2a0a43aefe59bc11f16445b5ee0c781179a33fa
ms.openlocfilehash: 1c136514f12749e9eac28bf4b4512acf3e8aaee1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="select-localvariable-transact-sql"></a>ВЫБЕРИТЕ @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Присваивает локальной переменной значение выражения.  
  
 Для назначения переменных рекомендуется использовать [ЗАДАТЬ @local_variable ](../../t-sql/language-elements/set-local-variable-transact-sql.md) вместо SELECT @*local_variable*.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SELECT { @local_variable { = | += | -= | *= | /= | %= | &= | ^= | |= } expression } 
    [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
@*local_variable*  
 Это объявленная переменная, которой должно быть присвоено значение.  
  
{= | += | -= | \*= | /= | %= | &= | ^= | |= }   
Присвоить значение справа переменной слева.  
  
Составной оператор присваивания:  
  |оператор |действие |   
  |-----|-----|  
  | = | Выражение, которое следует, назначается переменной. |  
  | += | Добавьте и назначьте |   
  | -= | Вычитание и присваивание |  
  | \*= | Умножение и назначение |  
  | /= | Деление и присваивание |  
  | %= | Остаток от деления и назначение |  
  | &= | Побитовое и и назначение |  
  | ^= | Побитовое исключающее или и присвоить |  
  | \|= | Побитовое или и присвоить |  
  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md). В их число также входит скалярный вложенный запрос.  
  
## <a name="remarks"></a>Замечания  
 SELECT @*local_variable* обычно используется для возвращения одного значения в переменной. Тем не менее, когда *выражение* имя столбца, могут возвращать несколько значений. Если инструкция SELECT возвращает более одного значения, переменной присваивается последнее возвращенное значение.  
  
 Если инструкция SELECT не возвращает ни одной строки, переменная сохраняет свое текущее значение. Если *выражение* является скалярным вложенным запросом, возвращает значение не переменная имеет значение NULL.  
  
 Одна инструкция SELECT может инициализировать несколько локальных переменных.  
  
> [!NOTE]  
>  Инструкция SELECT, содержащая назначение переменной, не может быть использована для выполнения операций по получению типичного результирующего набора.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-use-select-localvariable-to-return-a-single-value"></a>A. Инструкции SELECT @local_variable для возвращения одиночного значения  
 В следующем примере переменной `@var1` присвоено значение `Generic Name`. Запрос к таблице `Store` не возвращает строк, потому что в ней отсутствует значение, указанное для `CustomerID`. Переменная сохраняет значение `Generic Name`.  
  
```sql  
-- Uses AdventureWorks    
  
DECLARE @var1 varchar(30);         
SELECT @var1 = 'Generic Name';         
SELECT @var1 = Name         
FROM Sales.Store         
WHERE CustomerID = 1000 ;        
SELECT @var1 AS 'Company Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Company Name  
 ------------------------------  
 Generic Name  
 ```  
  
### <a name="b-use-select-localvariable-to-return-null"></a>Б. Инструкции SELECT @local_variable возвращает значение null  
 В следующем примере вложенный запрос используется для присвоения значения `@var1`. Так как значение, заданное для `CustomerID`, не существует, вложенный запрос не возвращает значение и переменная принимает значение `NULL`.  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @var1 varchar(30)   
SELECT @var1 = 'Generic Name'   
SELECT @var1 = (SELECT Name   
FROM Sales.Store   
WHERE CustomerID = 1000)   
SELECT @var1 AS 'Company Name' ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Company Name  
----------------------------  
NULL  
```  
  
## <a name="see-also"></a>См. также:  
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  

