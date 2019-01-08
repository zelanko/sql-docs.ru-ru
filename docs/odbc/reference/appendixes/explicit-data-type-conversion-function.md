---
title: Функция данных явные преобразования | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc229e2bef69069ba1fc5f8cb3077e592d959a55
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52521933"
---
# <a name="explicit-data-type-conversion-function"></a>Функция явного преобразования типа данных
Явного преобразования типов данных указывается с точки зрения определения типов данных SQL.  
  
 Синтаксис ODBC функцию преобразования типа данных явного ограничения не преобразования. Допустимость определенного преобразования одного типа в другой тип данных определяется Каждая реализация специфические для драйвера. Драйвер будет так как он преобразует синтаксис ODBC в собственном синтаксис, отклонять, когда, несмотря на то что юридические в синтаксисе ODBC не поддерживаются источником данных. Функции ODBC **SQLGetInfo**, с преобразованием параметров (например, SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH и т. д.), предоставляет способ запрос о преобразованиях, поддерживаемых источником данных .  
  
 Формат **преобразовать** функция:  
  
 **ПРЕОБРАЗОВАНИЕ (** *value_exp*, _data_type_**)**  
  
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
  
 Синтаксис ODBC функцию преобразования типа явные данных не поддерживает спецификацию преобразования формата. Если спецификация явного форматов поддерживается базовым источником данных, драйвер должен задавать значение по умолчанию или реализовать спецификации формата.  
  
 Аргумент *value_exp* может быть именем столбца, результат другую скалярную функцию, или числовое или строка литерала. Пример:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 Преобразует выход скалярной функции функция CURDATE в символьную строку.  
  
 Поскольку ODBC не требует тип данных для возвращаемых значений из скалярные функции (так как функции часто являются данными, зависящие от источника), приложения должны использовать скалярная функция CONVERT всякий раз, когда возможность принудительно выполнить преобразование типов данных.  
  
 В следующих двух примерах использования **преобразовать** функции. В этих примерах предполагается наличие таблицы с именем «EMPLOYEES» со столбцом EMPNO, типа SQL_SMALLINT и столбец EMPNAME типа SQL_CHAR.  
  
 Если приложение указывает следующую инструкцию SQL:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Драйвер для ORACLE переводит инструкцию SQL:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Driver для SQL Server преобразует инструкцию SQL:  
  
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
  
-   Driver для SQL Server преобразует инструкцию SQL:  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Драйвер Ingres переводит инструкцию SQL:  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
