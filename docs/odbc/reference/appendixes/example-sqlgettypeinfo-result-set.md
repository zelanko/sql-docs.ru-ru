---
title: Пример набора результатов S'LGetTypeInfo (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5cf62f8a95f4c91095c21a6d603317fe1f73500
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307015"
---
# <a name="example-sqlgettypeinfo-result-set"></a>Пример результирующего набора SQLGetTypeInfo
Приложение вызывает **S'LGetTypeInfo,** чтобы определить, какие типы данных поддерживаются источником данных и характеристиками этих типов данных. В следующих таблицах показан набор результатов, возвращенный **s'LGetTypeInfo** для источника данных, который поддерживает SQL_CHAR, SQL_LONGVARCHAR, SQL_DECIMAL, SQL_REAL, SQL_DATETIME, SQL_INTERVAL_YEAR и SQL_INTERVAL_DAY_TO_SECOND.  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|"символ"|SQL_CHAR|255|"'"|"'"|"длина"|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<Недействительный>|SQL_TRUE|  
|"десятичная"|SQL_DECIMAL|28|\<Недействительный>|\<Недействительный>|"точность,<br />масштаб"|SQL_TRUE|  
|"реальный"|SQL_REAL|7|\<Недействительный>|\<Недействительный>|\<Недействительный>|SQL_TRUE|  
|"Дата"|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<Недействительный>|SQL_TRUE|  
|"ИНТЕРВАЛ ГОД () В ГОД"|SQL_INTERVAL_YEAR|9|"'"|"'"|"точность"|SQL_TRUE|  
|"ИНТЕРВАЛ ДЕНЬ () К ФРАКЦИИ (5)"|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|"точность"|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<Недействительный>|SQL_FALSE|\<Недействительный>|"символ"|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<Недействительный>|SQL_FALSE|\<Недействительный>|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|"десятичная"|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|"реальный"|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<Недействительный>|SQL_FALSE|\<Недействительный>|"Дата"|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<Недействительный>|SQL_FALSE|\<Недействительный>|"ИНТЕРВАЛ ГОД () В ГОД"|  
|**SQL_INTERVAL_DAY_TO_SECOND**|SQL_FALSE|SQL_PRED_BASIC|\<Недействительный>|SQL_FALSE|\<Недействительный>|"ИНТЕРВАЛ ДЕНЬ () К ФРАКЦИИ (5)"|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<Недействительный>|\<Недействительный>|SQL_CHAR|\<Недействительный>|\<Недействительный>|\<Недействительный>|  
|**SQL_LONGVARCHAR**|\<Недействительный>|\<Недействительный>|SQL_LONGVARCHAR|\<Недействительный>|\<Недействительный>|\<Недействительный>|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<Недействительный>|10|\<Недействительный>|  
|**SQL_REAL**|\<Недействительный>|\<Недействительный>|SQL_REAL|\<Недействительный>|10|\<Недействительный>|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<Недействительный>|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<Недействительный>|9|  
|**SQL_INTERVAL_DAY_TO_SECOND**|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<Недействительный>|9|
