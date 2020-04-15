---
title: Функция преобразования явных типов данных (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306995"
---
# <a name="explicit-data-type-conversion-function"></a>Функция явного преобразования типа данных
Явная конверсия типа данных указана с точки зрения определений типа данных S'L.  
  
 Синтаксис ODBC для явной функции преобразования типа данных не ограничивает конверсии. Действительность конкретных конверсий одного типа данных в другой тип данных будет определяться каждой реализацией, конкретной драйвером. Драйвер, как это переводит синтаксис ODBC в родной синтаксис, отвергнет те преобразования, которые, хотя и законны в синтаксисе ODBC, не поддерживаются источником данных. Функция ODBC **s'LGetInfo,** с вариантами конверсии (например, SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH и т.д.), предоставляет возможность узнать о конверсиях, поддерживаемых источником данных.  
  
 Формат функции **CONVERT:**  
  
 **КОНВЕРТ** _(value_exp,_ _data_type)_**)**  
  
 Функция возвращает значение, указанное *value_exp* преобразовано в указанное *data_type,* где *data_type* является одним из следующих ключевых слов:  
  
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
  
 Синтаксис ODBC для явной функции преобразования типа данных не поддерживает спецификацию формата преобразования. Если спецификация явных форматов поддерживается базовым источником данных, драйвер должен указать значение по умолчанию или спецификацию формата реализации.  
  
 Аргументом *value_exp* может быть имя столбца, результат другой функции масштабирования, или числовая или строка буквально. Пример:  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 преобразует выход функции масштабирования CURDATE в строку символов.  
  
 Поскольку ODBC не требует типа данных для значений возврата от функций scalar (поскольку функции часто являются конкретными источниками данных), приложения должны использовать функцию масштабирования CONVERT, когда это возможно, чтобы заставить преобразование типа данных.  
  
 Следующие два примера иллюстрируют использование функции **CONVERT.** Эти примеры предполагают существование таблицы под названием EMPLOYEES, с столбцей типа EMPNO типа SQL_SMALLINT и столбцей eMPNAME типа SQL_CHAR.  
  
 Если в приложении указана следующая выписка по S'L:  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Драйвер для ORACLE переводит заявление S'L на:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Драйвер для сервера S'L переводит заявление S'L на:  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Если в приложении указана следующая выписка по S'L:  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Драйвер для ORACLE переводит заявление S'L на:  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Драйвер для сервера S'L переводит заявление S'L на:  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Драйвер для Ingres переводит заявление S'L на:  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
