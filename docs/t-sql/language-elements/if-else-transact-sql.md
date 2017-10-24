---
title: "IF... ELSE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/11/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IF_TSQL
- IF
dev_langs:
- TSQL
helpviewer_keywords:
- IF...ELSE keyword
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 676c881f-dee1-417a-bc51-55da62398e81
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ea7d020bc637ff2dda4ba0540de8385e99170cd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает условия для выполнения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)], следующая за ключевым словом IF и его условием, выполняется только в том случае, если логическое выражение возвращает TRUE. Необязательное ключевое слово ELSE представляет другую инструкцию языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которая выполняется, если условие IF не удовлетворяется и логическое выражение возвращает FALSE.  
  
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
 Выражение, возвращающее значение TRUE или FALSE. Если логическое выражение содержит инструкцию SELECT, инструкция SELECT должна быть заключена в скобки.  
  
 { *sql_statement*| *statement_block* }  
 Любая инструкция или группа инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], указанная с помощью блока инструкций. Без использования блока инструкций условия IF и ELSE могут повлиять на выполнение только одной инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Для определения блока инструкций используйте ключевые слова потока управления BEGIN и END.  
  
## <a name="remarks"></a>Замечания  
 Конструкция IF...ELSE может быть использована в пакетах, хранимых процедурах и нерегламентированных запросах. При использовании в хранимой процедуре эта конструкция часто применяется для проверки существования некоторого параметра.  
  
 Проверки IF могут находиться внутри другого IF или следующего ELSE. Ограничение количества вложенных уровней зависит от свободной памяти.  
  
## <a name="example"></a>Пример  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 Дополнительные примеры см. в разделе [ELSE &#40; Если... ELSE &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/else-if-else-transact-sql.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере используется `IF…ELSE` определите, какой из двух ответов для представления пользователю, на основе веса элемента в `DimProduct` таблицы.  
  
```  
-- Uses AdventureWorksDW  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct 
                  WHERE ProductKey = @productKey)   
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is too heavy to ship and is only available for pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
ELSE  
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is available for shipping or pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
```  
  
## <a name="see-also"></a>См. также:  
 [BEGIN... КОНЕЦ &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [КОНЕЦ &#40; BEGIN... КОНЕЦ &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ПОКА &#40; Transact-SQL &#41;](../../t-sql/language-elements/while-transact-sql.md)   
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Язык управления выполнением &#40; Transact-SQL &#41; ](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40; Если... ELSE &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  




