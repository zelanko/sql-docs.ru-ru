---
title: '| (побитовое ИЛИ) (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '|'
- '|_TSQL'
- Bitwise OR
- bitwise
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- OR operator
- bitwise OR (|)
- '| (bitwise OR operator)'
ms.assetid: 86a3b87f-9688-4eaf-a552-29f1b01d880a
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 49f60e5ed74df044e41699739eeb42acf5606b93
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982722"
---
# <a name="-bitwise-or-transact-sql"></a>| (Побитовое ИЛИ) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет побитовую логическую операцию OR для двух указанных целочисленных значений, которые преобразуются в двоичные выражения в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```   
expression | expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) категории целочисленных типов данных либо типа данных **bit**, **binary** или **varbinary**. *expression* трактуется как двоичное числовое значение для выполнения побитовой операции.  
  
> [!NOTE]  
>  В побитовой операции только одно выражение *expression* может иметь тип **binary** или **varbinary**.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает значение типа **int**, если входные значения имеют тип **int**, значение типа **smallint**, если входные значения имеют тип **smallint**, или значение типа **tinyint**, если входные значения имеют тип **tinyint**.  
  
## <a name="remarks"></a>Remarks  
 Побитовый оператор «|» выполняет логическую операцию OR над двумя выражениями, получая из них результат поразрядно. Каждый бит результата устанавливаются в 1, если хотя бы один из исходных битов равен 1. Если оба исходных бита равны 0, бит результата будет равен нулю.  
  
 Если левое и правое выражения принадлежат к различным целочисленным типам данных (например, левое выражение *expression* — к типу **smallint**, а правое выражение *expression* — к типу **int**), аргумент более короткого типа данных преобразовывается в более длинный тип данных. В этом примере **smallint**_expression_ преобразовывается в тип **int**.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере создается таблица с двумя столбцами исходных значений типа **int**, а затем в ней заполняется одна строка.  
  
```sql  
CREATE TABLE bitwise  
(   
 a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 Следующий запрос выполняет побитовую операцию ИЛИ со столбцами **a_int_value** и **b_int_value**.  
  
```  
SELECT a_int_value | b_int_value  
FROM bitwise;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
235           
  
(1 row(s) affected)  
```  
  
 Двоичное представление числа 170 (**a_int_value** или `A` ниже) равно `0000 0000 1010 1010`. Двоичное представление числа 75 (**b_int_value** или `B` ниже) равно `0000 0000 0100 1011`. При выполнении побитовой операции OR над этими двумя значениями получается двоичный результат `0000 0000 1110 1011`, что соответствует десятичному значению 235.  
  
```  
(A | B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 1110 1011  
```  
  
## <a name="see-also"></a>См. также:  
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы (Transact-SQL)](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [&#124;= (присваивание побитового ИЛИ) (Transact-SQL)](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


