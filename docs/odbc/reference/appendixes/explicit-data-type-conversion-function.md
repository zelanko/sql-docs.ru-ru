---
title: "Явное типов данных функции преобразования | Документы Microsoft"
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
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e0bba777a69607447428d83115c545edfeccec5d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="explicit-data-type-conversion-function"></a>Явный тип функции преобразования
Явного преобразования типов данных задается в рамках определения типов данных SQL.  
  
 Синтаксис ODBC функцию преобразования типа данных явного ограничения не преобразования. Каждая реализация драйвера будет определяться допустимость определенных преобразований из одного типа данных к другому типу данных. Драйвер как он преобразует синтаксис ODBC в native синтаксис отклонит этих преобразований, несмотря на то что допустимыми в синтаксис ODBC не поддерживается источником данных. Функция ODBC **SQLGetInfo**, с помощью преобразования параметры (например, SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH и т. д), позволяет запрашивать сведения о преобразованиях, поддерживаемых источником данных .  
  
 Формат **преобразовать** функции:  
  
 **ПРЕОБРАЗОВАНИЕ (** *value_exp*, *data_type***)**  
  
 Функция возвращает значение, заданное параметром *value_exp* преобразовать в указанный *data_type*, где *data_type* является одним из следующих ключевых слов:  
  
|||  
|-|-|  
|SQL_BIGINT|SQL_INTERVAL_HOUR_TO_MINUTE|  
|SQL_BINARY|SQL_INTERVAL_HOUR_TO_SECOND|  
|SQL_BIT|SQL_INTERVAL_MINUTE_TO_SECOND|  
|SQL_CHAR|SQL_LONGVARBINARY|  
|SQL_DECIMAL|SQL_LONGVARCHAR|  
|SQL_DOUBLE|SQL_NUMERIC|  
|SQL_FLOAT|SQL_REAL|  
|SQL_GUID|SQL_SMALLINT|  
|SQL_INTEGER|SQL_DATE|  
|SQL_INTERVAL_MONTH|SQL_TIME|  
|SQL_INTERVAL_YEAR|SQL_TIMESTAMP|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_TINYINT|  
|SQL_INTERVAL_DAY|SQL_VARBINARY|  
|SQL_INTERVAL_HOUR|SQL_VARCHAR|  
|SQL_INTERVAL_MINUTE|SQL_WCHAR|  
|SQL_INTERVAL_SECOND|SQL_WLONGVARCHAR|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_WVARCHAR|  
|SQL_INTERVAL_DAY_TO_MINUTE||  
|SQL_INTERVAL_DAY_TO_SECOND||  
  
 Синтаксис ODBC функцию преобразования типа явные данных не поддерживает спецификацию преобразования формата. Если спецификация явную форматов поддерживается в источнике данных, драйвер должен задавать значение по умолчанию или реализации спецификации формата.  
  
 Аргумент *value_exp* может быть имя столбца, результат другой скалярной функцией или numeric или строка литерала. Например:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 Преобразует выходные данные скалярной функции функция CURDATE в символьную строку.  
  
 Поскольку ODBC не требует тип данных для значения, возвращаемые из скалярные функции (так как функции часто являются данными, зависящее от источника), приложения должны использовать скалярная функция CONVERT всякий раз, когда возможно принудительное преобразование типов данных.  
  
 В следующих двух примерах показаны использование **преобразовать** функции. В этих примерах предполагается существование таблицу с именем СОТРУДНИКОВ, со столбцом EMPNO типа SQL_SMALLINT и столбец EMPNAME SQL_CHAR типа.  
  
 Если приложение указывает следующую инструкцию SQL:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Драйвер для ORACLE переводит инструкцию SQL:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Драйвер для SQL Server преобразует инструкцию SQL:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Если приложение указывает следующую инструкцию SQL:  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Драйвер для ORACLE переводит инструкцию SQL:  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Драйвер для SQL Server преобразует инструкцию SQL:  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Драйвер для Ingres переводит инструкцию SQL:  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```

