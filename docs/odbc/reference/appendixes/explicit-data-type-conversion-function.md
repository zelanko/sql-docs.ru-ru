---
title: Явная функция преобразования типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2de8a8cb6177e9210e8d48c0ce097d13c9a276fd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306995"
---
# <a name="explicit-data-type-conversion-function"></a>Функция явного преобразования типа данных
Явное преобразование типов данных указывается в терминах определений типов данных SQL.  
  
 Синтаксис ODBC для функции явного преобразования типа данных не ограничивает преобразования. Допустимость определенных преобразований одного типа данных в другой тип данных будет определяться каждой реализацией конкретного драйвера. Драйвер будет переводит синтаксис ODBC в собственный синтаксис, отклоните такие преобразования, которые, несмотря на синтаксис ODBC, не поддерживаются источником данных. Функция ODBC **SQLGetInfo**с параметрами преобразования (например, SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH и т. д.) предоставляет способ получения сведений о преобразованиях, поддерживаемых источником данных.  
  
 Формат функции **Convert** :  
  
 **Convert (** _value_exp_, _data_type_**)**  
  
 Функция возвращает значение, заданное *value_exp* , преобразованное в указанное *data_type*, где *data_type* является одним из следующих ключевых слов:  
  
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
  
 Синтаксис ODBC для функции явного преобразования типа данных не поддерживает спецификацию формата преобразования. Если в базовом источнике данных поддерживается спецификация явных форматов, драйвер должен указать значение по умолчанию или реализовать спецификацию формата.  
  
 Аргументом *value_exp* может быть имя столбца, результат другой скалярной функции или числовой или строковый литерал. Пример:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 Преобразует выходные данные скалярной функции CURDATE в символьную строку.  
  
 Поскольку ODBC не требует тип данных для возвращаемых значений скалярных функций (так как часто используются функции, относящиеся к источникам данных), приложения должны использовать скалярную функцию CONVERT везде, где это возможно, для принудительного преобразования типов данных.  
  
 В следующих двух примерах показано использование функции **Convert** . В этих примерах предполагается существование таблицы EMPLOYEEs со столбцом ЕМПНО типа SQL_SMALLINT и столбцом EMPNAME типа SQL_CHAR.  
  
 Если в приложении указана следующая инструкция SQL:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Драйвер для ORACLE преобразует инструкцию SQL в:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Драйвер для SQL Server преобразует инструкцию SQL в:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Если в приложении указана следующая инструкция SQL:  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Драйвер для ORACLE преобразует инструкцию SQL в:  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Драйвер для SQL Server преобразует инструкцию SQL в:  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Драйвер для входной переменной преобразует инструкцию SQL в:  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
