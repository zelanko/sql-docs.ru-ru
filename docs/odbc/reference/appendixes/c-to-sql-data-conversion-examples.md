---
title: C, чтобы примеры преобразования данных SQL | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcba6d92970d0e0b5490f4c24506fe8bb2951217
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906359"
---
# <a name="c-to-sql-data-conversion-examples"></a>C, чтобы примеры преобразования данных SQL
В следующих примерах показано, как драйвер преобразует данных C к данным SQL:  
  
|Идентификатор типа C|Значение данных C|Тип SQL<br /><br /> идентификатор|Столбец<br /><br /> length|SQL-данные<br /><br /> value|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 []|SQL_CHAR|6|abcdef|н/д|  
|SQL_C_CHAR|abcdef\0 []|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56\0 []|SQL_DECIMAL|8 [b]|1234.56|н/д|  
|SQL_C_CHAR|1234.56\0 []|SQL_DECIMAL|7 [b]|1234.5|22001|  
|SQL_C_CHAR|1234.56\0 []|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|н/д|1234.56|н/д|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|н/д|1 234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|н/д|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_CHAR|10|1992-12-31|н/д|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 [c]|SQL_TIMESTAMP|н/д|1992-12-31 00:00:00.0|н/д|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|н/д|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [] «\0» представляет байт конечное значение null. Байтов конечное значение null является обязательным, только если длина данных SQL_NTS.  
  
 [b] в дополнение к байт для чисел для входа требуется один байт, а другой байтов необходим для десятичной запятой.  
  
 [c] чисел в этот список — это числа, хранящиеся в полях структуры SQL_DATE_STRUCT.  
  
 [d] чисел в этот список — это числа, хранящиеся в полях структуры SQL_TIMESTAMP_STRUCT.
