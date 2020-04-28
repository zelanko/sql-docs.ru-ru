---
title: Примеры преобразования данных C в SQL | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e21654f183946675c63cee10a3c08754e1508f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81291994"
---
# <a name="c-to-sql-data-conversion-examples"></a>Примеры преобразования данных из C в SQL
В следующих примерах показано, как драйвер преобразует данные C в данные SQL:  
  
|Идентификатор типа C|Значение данных C|Тип SQL<br /><br /> идентификатор|Столбец<br /><br /> length|SQL-данные<br /><br /> значение|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|6|abcdef|Недоступно|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|5|ABCDE|22001|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|8 [b]|1234,56|Недоступно|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|7 [b]|1234,5|22001|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234,56|SQL_FLOAT|Недоступно|1234,56|Недоступно|  
|SQL_C_FLOAT|1234,56|SQL_INTEGER|Недоступно|1 234|22001|  
|SQL_C_FLOAT|1234,56|SQL_TINYINT|Недоступно|----|22003|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_CHAR|10|1992-12-31|Недоступно|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_TIMESTAMP|Недоступно|1992-12-31 00:00:00.0|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [a] "\ 0" представляет байт завершения null. Байты с завершающим нулем требуется только в том случае, если длина данных SQL_NTS.  
  
 [b] в дополнение к байтам для чисел требуется один байт для знака, а для десятичной запятой требуется другой байт.  
  
 [c] числа в этом списке являются числами, хранящимися в полях структуры SQL_DATE_STRUCT.  
  
 [d] числа в этом списке являются числами, хранящимися в полях структуры SQL_TIMESTAMP_STRUCT.
