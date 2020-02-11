---
title: Вызовы скалярной функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37209a75c03a051e3def4d26fa0d4e7f85d0e91d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67897751"
---
# <a name="scalar-function-calls"></a>Вызовы скалярных функций
Скалярные функции возвращают значение для каждой строки. Например, скалярная функция абсолютного значения принимает числовой столбец в качестве аргумента и возвращает абсолютное значение каждого значения в столбце. Escape-последовательность для вызова скалярной функции:  
  
 **{fn**,_Скалярная функция_ **}**    
  
 где *Скалярная функция* — одна из функций, перечисленных в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Дополнительные сведения о escape-последовательности скалярной функции см. в разделе [escape-последовательность скалярной функции](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) в приложении C: грамматика SQL.  
  
 Например, следующие инструкции SQL создают одинаковый результирующий набор имен клиентов в верхнем регистре. В первой инструкции используется синтаксис escape-последовательности. Во втором операторе используется собственный синтаксис для входных данных OS/2, который не поддерживает взаимодействие.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Приложение может смешивать вызовы скалярных функций, использующих собственный синтаксис и вызовы скалярных функций, использующих синтаксис ODBC. Например, предположим, что имена в таблице Employee хранятся в виде фамилии, запятой и имени. Следующая инструкция SQL создает результирующий набор фамилий сотрудников в таблице Employee. Инструкция использует **ПОДстроку** скалярной функции ODBC и SQL Server скалярную функцию **charIndex** и будет правильно выполняться только в SQL Server.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Для обеспечения максимальной совместимости приложения должны использовать скалярную функцию **Convert** , чтобы убедиться, что выходные данные скалярной функции являются требуемым типом. Функция **Convert** преобразует данные из одного типа данных SQL в указанный тип данных SQL. Синтаксис функции **Convert**  
  
 **Convert (** _value_exp_ **,** _data_type_**)**  
  
 где *value_exp* — это имя столбца, результат другой скалярной функции или литеральное значение, а *data_type* — это ключевое слово, совпадающее с именем **#define** , которое используется идентификатором типа данных SQL, как определено в [приложении D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md). Например, следующая инструкция SQL использует функцию **Convert** , чтобы убедиться, что выходные данные функции **CURDATE** являются датой, а не символьными данными или символами-метками:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Чтобы определить, какие скалярные функции поддерживаются источником данных, приложение вызывает **SQLGetInfo** с параметрами SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS и SQL_TIMEDATE_FUNCTIONS. Чтобы определить, какие операции преобразования поддерживаются функцией **Convert** , приложение вызывает **SQLGetInfo** с любыми параметрами, начинающимися с SQL_CONVERT.
