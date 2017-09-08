---
title: "STUFF (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: df9a3d019f22ec8a0ba610f2dd694e45a8bd9da3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="stuff-transact-sql"></a>STUFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Функция STUFF вставляет одну строку в другую. Она удаляет указанное количество символов первой строки в начальной позиции и вставляет на их место вторую строку.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STUFF ( character_expression , start , length , replaceWith_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных данных. *character_expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
 *Запуск*  
 Целочисленное значение, определяющее место начала удаления и вставки. Если *запустить* или *длина* имеет отрицательное значение, возвращается пустая строка. Если *запустить* длиннее, чем первый *character_expression*, возвращается пустая строка. *Запуск* может иметь тип **bigint**.  
  
 *length*  
 Целочисленное выражение, которое определяет, какое количество символов следует удалить. Если *длина* длиннее, чем первый *character_expression*, удаление выполняется до до последнего символа в последнем *character_expression*. *Длина* может иметь тип **bigint**.  
  
 *replaceWith_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных данных. *character_expression* может быть константой, переменной или столбцом символьных или двоичных данных. Это выражение заменяет *длина* символов *character_expression* начиная *запустить*. Предоставление `NULL` как *replaceWith_expression*, удаляет знаки без вставки ничего.   
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает символьные данные, если *character_expression* является одним из поддерживаемых символьных типов данных. Возвращает двоичные данные, если *character_expression* является одним из поддерживаемых двоичных типов данных.  
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  

