---
title: SQL, чтобы примеры преобразования данных C | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a2fa699cb8d57e9ec44ec133ec766b70414e00b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-to-c-data-conversion-examples"></a>SQL, чтобы примеры преобразования данных C
Примеры, приведенные в следующей таблице показано, как драйвер преобразует данные SQL для данных C:  
  
|Тип SQL<br /><br /> идентификатор|SQL-данные<br /><br /> value|Тип C<br /><br /> идентификатор|Буфер<br /><br /> length|**TargetValuePtr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0 []|н/д|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0 []|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56\0 []|н/д|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234\0 []|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|не учитывается|1234.56|н/д|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|не учитывается|1 234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|не учитывается|----|22003|  
SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|не учитывается|1.2345678|н/д|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|не учитывается|1.234567|н/д|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|не учитывается|1|н/д|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31\0 []|н/д|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|не учитывается|1992,12,31, 0,0,0,0 [b]|н/д|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12\0 []|н/д|  
SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55.1\0 []|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 [] «\0» представляет байт конечное значение null. Драйвер всегда null завершает данные SQL_C_CHAR.  
  
 [b] чисел в этот список — это числа, хранящиеся в полях структуры TIMESTAMP_STRUCT.
