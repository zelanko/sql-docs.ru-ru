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
ms.openlocfilehash: ed0a1e9155eeb3e2147bed3dd31e78176bdc38d2
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363324"
---
# <a name="explicit-data-type-conversion-function"></a>Функция явного преобразования типа данных
Явное преобразование типов данных указывается в терминах определений типов данных SQL.  
  
 Синтаксис ODBC для функции явного преобразования типа данных не ограничивает преобразования. Допустимость определенных преобразований одного типа данных в другой тип данных будет определяться каждой реализацией конкретного драйвера. Драйвер будет переводит синтаксис ODBC в собственный синтаксис, отклоните такие преобразования, которые, несмотря на синтаксис ODBC, не поддерживаются источником данных. Функция ODBC **SQLGetInfo**с параметрами преобразования (например, SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH и т. д.) предоставляет способ получения сведений о преобразованиях, поддерживаемых источником данных.  
  
 Формат функции **Convert** :  
  
 **Convert (** _value_exp_, _data_type_**)**  
  
 Функция возвращает значение, заданное *value_exp* , преобразованное в указанное *data_type*, где *data_type* является одним из следующих ключевых слов:  

:::row:::
    :::column:::
        SQL_BIGINT  
        SQL_BINARY  
        SQL_BIT  
        SQL_CHAR  
        SQL_DATE  
        SQL_DECIMAL  
        SQL_DOUBLE  
        SQL_FLOAT  
        SQL_GUID  
        SQL_INTEGER  
        SQL_INTERVAL_DAY  
        SQL_INTERVAL_DAY_TO_HOUR  
    :::column-end:::
    :::column:::
        SQL_INTERVAL_DAY_TO_MINUTE  
        SQL_INTERVAL_DAY_TO_SECOND  
        SQL_INTERVAL_HOUR  
        SQL_INTERVAL_HOUR_TO_MINUTE  
        SQL_INTERVAL_HOUR_TO_SECOND  
        SQL_INTERVAL_MINUTE  
        SQL_INTERVAL_MINUTE_TO_SECOND  
        SQL_INTERVAL_MONTH  
        SQL_INTERVAL_SECOND  
        SQL_INTERVAL_YEAR  
        SQL_INTERVAL_YEAR_TO_MONTH  
        SQL_LONGVARBINARY  
    :::column-end:::
    :::column:::
        SQL_LONGVARCHAR  
        SQL_NUMERIC  
        SQL_REAL  
        SQL_SMALLINT  
        SQL_TIME  
        SQL_TIMESTAMP  
        SQL_TINYINT  
        SQL_VARBINARY  
        SQL_VARCHAR  
        SQL_WCHAR  
        SQL_WLONGVARCHAR  
        SQL_WVARCHAR  
    :::column-end:::
:::row-end:::

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
