---
title: Пример результатов SQLGetTypeInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], examples
- SQLGetTypeInfo function [ODBC], examples
- data types [ODBC], SQL data types
ms.assetid: dc1952cc-7581-4d69-9c72-7dc1cd370836
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 028b9be01439b122ff164aed68adb40eb1b4a46e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662622"
---
# <a name="example-sqlgettypeinfo-result-set"></a>Пример результирующего набора SQLGetTypeInfo
Приложение вызывает **SQLGetTypeInfo** для определения, какие типы данных поддерживаются источником данных и характеристики этих типов данных. В следующих таблицах приведены образец результирующего набора, возвращенный **SQLGetTypeInfo** для источника данных, который поддерживает SQL_CHAR, SQL_LONGVARCHAR, SQL_DECIMAL, SQL_REAL, SQL_DATETIME, SQL_INTERVAL_YEAR и SQL_INTERVAL_DAY_TO_SECOND.  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|«char»|SQL_CHAR|255|"'"|"'"|«Длина»|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<NULL >|SQL_TRUE|  
|«десятичное число»|SQL_DECIMAL|28|\<NULL >|\<NULL >|«точность,<br />Масштаб»|SQL_TRUE|  
|«настоящих»|SQL_REAL|7|\<NULL >|\<NULL >|\<NULL >|SQL_TRUE|  
|«datetime»|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<NULL >|SQL_TRUE|  
|«ИНТЕРВАЛ YEAR() ГОД»|SQL_INTERVAL_YEAR|9|"'"|"'"|«точность»|SQL_TRUE|  
|«ИНТЕРВАЛ DAY() ДЛЯ FRACTION(5)»|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|«точность»|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<NULL >|SQL_FALSE|\<NULL >|«char»|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<NULL >|SQL_FALSE|\<NULL >|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|«десятичное число»|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|«настоящих»|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<NULL >|SQL_FALSE|\<NULL >|«datetime»|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<NULL >|SQL_FALSE|\<NULL >|«ИНТЕРВАЛ YEAR() ГОД»|  
TERVAL_DAY_TO_SECOND**|SQL_FALSE|SQL_PRED_BASIC|\<NULL >|SQL_FALSE|\<NULL >|«ИНТЕРВАЛ DAY() ДЛЯ FRACTION(5)»|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<NULL >|\<NULL >|SQL_CHAR|\<NULL >|\<NULL >|\<NULL >|  
|**SQL_LONGVARCHAR**|\<NULL >|\<NULL >|SQL_LONGVARCHAR|\<NULL >|\<NULL >|\<NULL >|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<NULL >|10|\<NULL >|  
|**SQL_REAL**|\<NULL >|\<NULL >|SQL_REAL|\<NULL >|10|\<NULL >|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<NULL >|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<NULL >|9|  
ERVAL_DAY_TO_SECOND**|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<NULL >|9|
