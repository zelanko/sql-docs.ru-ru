---
title: "Money и smallmoney (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- money_TSQL
- money
- smallmoney
- smallmoney_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- money data type, about money data type
- money data type
- smallmoney data type
- values [SQL Server], monetary
- currency [SQL Server]
ms.assetid: 57861137-89ea-4b89-b361-390597d7bccc
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bd07ecd1cdacc686e0f831320fd5e939c0c174da
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="money-and-smallmoney-transact-sql"></a>Типы money и smallmoney (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы данных, представляющие денежные (валютные) значения.
  
## <a name="remarks"></a>Замечания  
  
|Тип данных|Диапазон|Память|  
|---|---|---|
|**money**|-922,337,203,685,477.5808 для 922,337,203,685,477.5807 (-922,337,203,685,477.58<br />Чтобы 922,337,203,685,477.58 для Informatica.  Informatica поддерживает только два десятичных знака, не четыре.)|8 байт|  
|**smallmoney**|От -214 748,3648 до 214 748,3647|4 байта|  
  
**Money** и **smallmoney** типов данных точность до одной десятитысячной денежной единицы, которые они представляют. Для Informatica **money** и **smallmoney** типы данных имеют точность до одну сотую денежные единицы, которые они представляют.
  
Чтобы отделить дробные денежные единицы, например центы, от целых денежных единиц, используйте запятую. Например, 2,15 соответствует 2 долларам и 15 центам.
  
Для этих типов данных может использоваться любой из следующих символов валют.
  
![Таблица символов валют, шестнадцатеричные значения](../../t-sql/data-types/media/money01.gif "таблица символов валют, шестнадцатеричные значения")
  
Валютные или денежные данные не требуется заключать в одинарные кавычки ( ' ). Важно помнить, что, несмотря на возможность указания денежных значений, которым предшествует символ валюты, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сохраняет какие-либо сведения о валюте, связанные с символом, а хранит только числовое значение.
  
## <a name="converting-money-data"></a>Преобразование данных money
При преобразовании в **money** из целочисленных типов данных, единицы измерения считаются денежные единицы. Например, целочисленное значение 4 преобразуется в **money** эквивалентное 4 денежные единицы.
  
В следующем примере выполняется преобразование **smallmoney** и **money** значения **varchar** и **десятичное** соответственно.
  
```sql
DECLARE @mymoney_sm smallmoney = 3148.29,  
        @mymoney    money = 3148.29;  
SELECT  CAST(@mymoney_sm AS varchar) AS 'SM_MONEY varchar',  
        CAST(@mymoney AS decimal)    AS 'MONEY DECIMAL';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
SM_MONEY VARCHAR               MONEY DECIMAL  
------------------------------ ----------------------  
3148.29                        3148    
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[Инструкция ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md) 
 [CAST и CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md) 
 [Создание таблицы &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md) 
 [Типы данных &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md) 
 [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
 [ЗАДАТЬ @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md) 
 [sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

