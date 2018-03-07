---
title: "STUFF (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STUFF
- STUFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting characters
- STUFF function
- length characters
- removing characters
- replacing characters
- characters [SQL Server], replacing
- inserting data
ms.assetid: abb0afa9-44f6-42a2-a871-5f471dfb222b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 10edb8b1b1e3008321bc03e2e65419dca8956f86
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="stuff-transact-sql"></a>STUFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Функция STUFF вставляет одну строку в другую. Она удаляет указанное количество символов первой строки в начальной позиции и вставляет на их место вторую строку.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STUFF ( character_expression , start , length , replaceWith_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных данных. *character_expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
 *start*  
 Целочисленное значение, определяющее место начала удаления и вставки. Если *запустить* является отрицательным, или ноль, возвращается пустая строка. Если *запустить* длиннее, чем первый *character_expression*, возвращается пустая строка. *Запуск* может иметь тип **bigint**.  
  
 *длина*  
 Целочисленное выражение, которое определяет, какое количество символов следует удалить. Если *длина* имеет отрицательное значение, возвращается пустая строка. Если *длина* длиннее, чем первый *character_expression*, удаление выполняется до до последнего символа в последнем *character_expression*.  Если *длина* равен нулю, вставка не производится до первого символа в строке. *Длина* может иметь тип **bigint**.

 *replaceWith_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных данных. *character_expression* может быть константой, переменной или столбцом символьных или двоичных данных. Это выражение заменяет *длина* символов *character_expression* начиная *запустить*. Предоставление `NULL` как *replaceWith_expression*, удаляет знаки без вставки ничего.   
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает символьные данные, если *character_expression* является одним из поддерживаемых символьных типов данных. Возвращает двоичные данные, если *character_expression* является одним из поддерживаемых двоичных типов данных.  
  
## <a name="remarks"></a>Remarks  
 Если начальная позиция или число удаляемых символов отрицательны или если начальная позиция превышает длину первой строки, возвращается пустая строка. Если начальная позиция равна 0, то возвращается значение NULL. Если число удаляемых символов превышает длину первой строки, удаление выполняется до первого символа первой строки.  

Ошибка, которая возникает, если результат больше, чем максимальное значение, поддерживаемое типом возвращаемого параметра.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 При использовании параметров сортировки SC, оба *character_expression* и *replaceWith_expression* могут содержать суррогатные пары. Параметр длины подсчитывает каждый суррогат *character_expression* как один символ.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует создание строки `abcdef` после удаления из нее трех символов, начиная с позиции `2`, с символа `b` и вставки второй строки в место удаления.  
  
```  
SELECT STUFF('abcdef', 2, 3, 'ijklmn');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
aijklmnef   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также  
 [CONCAT &#40; Transact-SQL &#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [Функция FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40; Transact-SQL &#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [Заменить &#40; Transact-SQL &#41;](../../t-sql/functions/replace-transact-sql.md)  
 [ОБРАТИТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40; Transact-SQL &#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [ПРЕОБРАЗОВАТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
