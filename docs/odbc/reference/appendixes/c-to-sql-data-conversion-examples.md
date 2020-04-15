---
title: Примеры преобразования данных от C до S'L (примеры» (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291994"
---
# <a name="c-to-sql-data-conversion-examples"></a>Примеры преобразования данных из C в SQL
Следующие примеры иллюстрируют, как драйвер преобразует данные C в данные S'L:  
  
|Идентификатор типа C|Значение C данных|Тип SQL<br /><br /> идентификатор|Столбец<br /><br /> length|SQL-данные<br /><br /> значение|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef'0 'a)|SQL_CHAR|6|abcdef|Недоступно|  
|SQL_C_CHAR|abcdef'0 'a)|SQL_CHAR|5|Abcde|22001|  
|SQL_C_CHAR|1234.56 х 0|SQL_DECIMAL|8-й день|1234.56|Недоступно|  
|SQL_C_CHAR|1234.56 х 0|SQL_DECIMAL|7-b.|1234.5|22001|  
|SQL_C_CHAR|1234.56 х 0|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|Недоступно|1234.56|Недоступно|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|Недоступно|1 234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|Недоступно|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31|SQL_CHAR|10|1992-12-31|Недоступно|  
|SQL_C_TYPE_DATE|1992,12,31|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31|SQL_TIMESTAMP|Недоступно|1992-12-31 00:00:00.0|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000|SQL_CHAR|22|1992-12-31 23:45:55.12|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000|SQL_CHAR|18|----|22003|  
  
 «З0» представляет собой байт с нулевым прекращением. Байт с нулевым прекращением требуется только в том случае, если длина данных SQL_NTS.  
  
 В дополнение к байтам для чисел, один байт требуется для знака, а другой байт требуется для десятичной точки.  
  
 Цифры в этом списке — это числа, хранящиеся в полях SQL_DATE_STRUCT структуры.  
  
 Цифры в этом списке — это числа, хранящиеся в полях структуры SQL_TIMESTAMP_STRUCT.
