---
title: C, чтобы примеры преобразования данных SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40cd9973bfdce68b1ccbe63edd8c875519dbd22b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63201590"
---
# <a name="c-to-sql-data-conversion-examples"></a>Примеры преобразования данных из C в SQL
В следующих примерах показано, как драйвер преобразует данных C в данных SQL:  
  
|Идентификатор типа C|Значение данных C|Тип SQL<br /><br /> идентификатор|Столбец<br /><br /> length|SQL-данные<br /><br /> value|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|6|abcdef|н/д|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|8 [b]|1234.56|н/д|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|7 [b]|1234.5|22001|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|н/д|1234.56|н/д|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|н/д|1 234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|н/д|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_CHAR|10|1992-12-31|н/д|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_TIMESTAMP|н/д|1992-12-31 00:00:00.0|н/д|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|н/д|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [a] «\0» представляет байт конечное значение null. Байтов конечное значение null является обязательным только в том случае, если длина данных составляет SQL_NTS.  
  
 [b] в дополнение к байт для чисел один байт является обязательным для входа и другой байтов является обязательным для десятичной запятой.  
  
 [c] числа в этот список — это числа, хранящиеся в полях SQL_DATE_STRUCT структуры.  
  
 [d] числа в этот список — это числа, хранящиеся в полях структуры SQL_TIMESTAMP_STRUCT.
