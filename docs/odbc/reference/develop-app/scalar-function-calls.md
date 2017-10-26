---
title: "Скалярная функция вызывает | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3fb62d7c916584da7411f398f66a2acf134bfa24
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="scalar-function-calls"></a>Вызовы скалярных функций
Скалярные функции возвращают значение для каждой строки. Например скалярная функция абсолютное значение числового столбца в качестве аргумента принимает и возвращает абсолютное значение каждого значения в столбце. Escape-последовательность для вызова скалярной функции  
  
 **{fn***скалярная функция* **}  **  
  
 где *скалярная функция* — одна из функций, перечисленных в [приложение E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md). Дополнительные сведения об escape-последовательность скалярной функции в разделе [скалярные функции Escape-последовательность](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) в грамматику SQL приложение C:.  
  
 Например следующие инструкции SQL создать тот же результирующий набор клиенту верхнего регистра имен. В первом операторе используется синтаксис escape последовательность. Вторая инструкция использует собственный синтаксис для Ingres для OS/2 и не поддерживает взаимодействие.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Приложение можно смешивать вызовы для скалярных функций, которые используют собственный синтаксис и вызовы скалярных функций, которые используют синтаксис ODBC. Например предположим, что имена в таблице Employee хранятся в виде фамилия, запятая и имя. Следующая инструкция SQL создает результирующий набор из фамилий сотрудников в таблице сотрудников. Инструкция использует скалярные функции ODBC **ПОДСТРОКИ** и скалярную функцию SQL Server **CHARINDEX** и будет правильно выполняться только на сервере SQL Server.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) – 1)} FROM Customers  
```  
  
 Для максимальной совместимости приложения должны использовать **преобразовать** скалярную функцию, чтобы убедиться в том, что скалярная функция является требуемого типа. **Преобразовать** функция преобразует данные из одного типа данных SQL в указанный тип данных SQL. Синтаксис **преобразовать** функция  
  
 **ПРЕОБРАЗОВАНИЕ (** *value_exp* **,** *data_type***)**  
  
 где *value_exp* является имя столбца, в результате другой скалярной функции или значение литерала и *data_type* ключевое слово, которое соответствует **#define** имя, используемое по Идентификатор типа данных SQL, как определено в [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md). Например, следующая инструкция SQL использует **преобразовать** функции, чтобы убедиться в том, что выходные данные **функция CURDATE** функция — это дата, вместо данных отметки времени или символ:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Чтобы определить, скалярные функции, которые поддерживаются источником данных, приложение вызывает **SQLGetInfo** SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS и SQL_TIMEDATE_ Параметры функции. Чтобы определить какие операции преобразования, поддерживаемые **преобразовать** приложение вызывает функцию, **SQLGetInfo** с одним из параметров, которые начинаются с SQL_CONVERT.

