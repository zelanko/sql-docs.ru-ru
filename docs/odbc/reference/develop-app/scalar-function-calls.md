---
title: Вызовы функции scalar (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349599a51b2996f419e6c8656a71bc9e30146542
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304265"
---
# <a name="scalar-function-calls"></a>Вызовы скалярных функций
Функции Scalar возвращают значение для каждой строки. Например, функция абсолютного значения масштабирования использует числовой столбец в качестве аргумента и возвращает абсолютное значение каждого значения в столбце. Последовательность побега для вызова функции масштабирования  
  
 **«Fn**_scalar-функция»_ **}**    
  
 где *масштабная функция* является одной из функций, перечисленных в [приложении E: Scalar Functions.](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md) Для получения дополнительной информации о последовательности [Scalar Function Escape Sequence](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) побега функции масштабирования см.  
  
 Например, следующие операторы S'L создают один и тот же набор результатов имен клиентов верхнего регистра. В первом заявлении используется синтаксис побега-последовательности. Второе утверждение использует родной синтаксис для Ingres для OS/2 и не совместимо.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Приложение может смешивать вызовы в масштабированные функции, которые используют нативный синтаксис, и вызовы на масштабальные функции, которые используют синтаксис ODBC. Например, предположим, что имена в таблице сотрудника хранятся как фамилия, запятая и имя. Следующее заявление S'L создает набор итоговых имен сотрудников в таблице сотрудника. В заявлении используется функция масштабирования ODBC **SUBSTRING** и функция s'L Server **scalar CHARINDEX** и будет правильно выполняться только на сервере S'L.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Для максимальной совместимости приложения должны использовать функцию **масштабирования CONVERT,** чтобы убедиться, что выход функции скалара является необходимым типом. Функция **CONVERT** преобразует данные из одного типа данных S'L в указанный тип данных S'L. Синтаксис функции **CONVERT**  
  
 **КОНВЕРТ** _(value_exp,_ **,** _data_type)_**)**  
  
 если *value_exp* — это имя столбца, результат другой функции масштабирования или буквальное значение, и *data_type* является ключевым словом, которое соответствует **#define** имени, используемому идентификатором типа данных, как это определено в [приложении D: Типы данных.](../../../odbc/reference/appendixes/appendix-d-data-types.md) Например, в следующем заявлении S'L используется функция **CONVERT,** чтобы убедиться, что вывод функции **CURDATE** является датой, а не меткой времени или данными символов:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Чтобы определить, какие функции масштабирования поддерживаются источником данных, приложение вызывает **s'LGetInfo** с SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS и SQL_TIMEDATE_FUNCTIONS опций. Чтобы определить, какие операции преобразования поддерживаются функцией **CONVERT,** приложение вызывает **S'LGetInfo** с любым из вариантов, которые начинаются с SQL_CONVERT.
