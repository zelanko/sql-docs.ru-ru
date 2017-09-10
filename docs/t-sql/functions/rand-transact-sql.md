---
title: "Функция RAND (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1d358122487d3568167021ac3a296e1eb2d1974
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Возвращает псевдослучайные **float** значение от 0 до 1.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Начальное значение*  
 Должно быть целым числом [выражение](../../t-sql/language-elements/expressions-transact-sql.md) (**tinyint**, **smallint**, или **int**), задающее начальное значение. Если *начальное значение* не указан, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] присваивает случайно выбранное начальное значение. Для указанного начального значения возвращаемый результат всегда будет один и тот же.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **float**  
  
## <a name="remarks"></a>Замечания  
 Повторные вызовы RAND() с одинаковым начальным значением возвращают одинаковые результаты.  
  
 Для одного соединения, если RAND() вызван с конкретным начальным значением, все последующие вызовы RAND() выдадут результат, основанный на начальном вызове RAND(). Например, следующий запрос всегда будет возвращать ту же последовательность чисел.  
  
```  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>Примеры  
 Следующий пример выдает четыре различных случайных числа, сформированных функцией RAND.  
  
```  
DECLARE @counter smallint;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
