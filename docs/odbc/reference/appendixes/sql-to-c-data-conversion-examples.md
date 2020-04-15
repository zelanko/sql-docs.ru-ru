---
title: Примеры преобразования данных в C Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b10dd93c807aaa49a7e10e198f789fb47ccdeb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296654"
---
# <a name="sql-to-c-data-conversion-examples"></a>Примеры преобразования данных из SQL в C

Примеры, приведенные в следующей таблице, иллюстрируют, как драйвер преобразует данные S'L в c-данные:  
  
|Тип SQL<br /><br /> идентификатор|SQL-данные<br /><br /> значение|Тип C<br /><br /> идентификатор|Буфер<br /><br /> length|**TargetValuePtr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef'0 'a)|Недоступно|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde'0|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56 х 0|Недоступно|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234 х 0|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|не учитывается|1234.56|Недоступно|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|не учитывается|1 234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|не учитывается|----|22003|  
|SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|не учитывается|1.2345678|Недоступно|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|не учитывается|1.234567|Недоступно|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|не учитывается|1|Недоступно|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31-0|Недоступно|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|не учитывается|1992,12,31, 0,0,0,0|Недоступно|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12|Недоступно|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55.1|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 «З0» представляет собой байт с нулевым прекращением. Водитель всегда сводит на нет SQL_C_CHAR данные.  
  
 Цифры в этом списке — это числа, хранящиеся в полях структуры TIMESTAMP_STRUCT.
