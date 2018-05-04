---
title: Пример результатов SQLGetTypeInfo | Документы Microsoft
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
- SQL data types [ODBC], examples
- SQLGetTypeInfo function [ODBC], examples
- data types [ODBC], SQL data types
ms.assetid: dc1952cc-7581-4d69-9c72-7dc1cd370836
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 113dfa21be16df908280d896638acd30fcd0d0e5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="example-sqlgettypeinfo-result-set"></a>Пример SQLGetTypeInfo результирующего набора
Приложение вызывает **SQLGetTypeInfo** для определения, какие типы данных поддерживаются источником данных и характеристики этих типов данных. В следующих таблицах показаны образец результирующего набора, возвращаемого **SQLGetTypeInfo** для источника данных, который поддерживает SQL_CHAR, SQL_LONGVARCHAR, SQL_DECIMAL, SQL_REAL, SQL_DATETIME, SQL_INTERVAL_YEAR и SQL_INTERVAL_DAY_TO_SECOND.  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|«char»|SQL_CHAR|255|"'"|"'"|«Длина»|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<Значение NULL >|SQL_TRUE|  
|«десятичное число»|SQL_DECIMAL|28|\<Значение NULL >|\<Значение NULL >|«точность и<br />Масштаб»|SQL_TRUE|  
|«real»|SQL_REAL|7|\<Значение NULL >|\<Значение NULL >|\<Значение NULL >|SQL_TRUE|  
|«datetime»|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<Значение NULL >|SQL_TRUE|  
|«ИНТЕРВАЛ YEAR() ГОД»|SQL_INTERVAL_YEAR|9|"'"|"'"|«точность»|SQL_TRUE|  
|«ИНТЕРВАЛ DAY() ДЛЯ FRACTION(5)»|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|«точность»|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<Значение NULL >|SQL_FALSE|\<Значение NULL >|«char»|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<Значение NULL >|SQL_FALSE|\<Значение NULL >|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|«десятичное число»|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|«real»|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<Значение NULL >|SQL_FALSE|\<Значение NULL >|«datetime»|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<Значение NULL >|SQL_FALSE|\<Значение NULL >|«ИНТЕРВАЛ YEAR() ГОД»|  
TERVAL_DAY_TO_SECOND**|SQL_FALSE|SQL_PRED_BASIC|\<Значение NULL >|SQL_FALSE|\<Значение NULL >|«ИНТЕРВАЛ DAY() ДЛЯ FRACTION(5)»|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<Значение NULL >|\<Значение NULL >|SQL_CHAR|\<Значение NULL >|\<Значение NULL >|\<Значение NULL >|  
|**SQL_LONGVARCHAR**|\<Значение NULL >|\<Значение NULL >|SQL_LONGVARCHAR|\<Значение NULL >|\<Значение NULL >|\<Значение NULL >|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<Значение NULL >|10|\<Значение NULL >|  
|**SQL_REAL**|\<Значение NULL >|\<Значение NULL >|SQL_REAL|\<Значение NULL >|10|\<Значение NULL >|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<Значение NULL >|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<Значение NULL >|9|  
ERVAL_DAY_TO_SECOND**|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<Значение NULL >|9|
