---
description: Пример результирующего набора SQLGetTypeInfo
title: Пример результирующего набора SQLGetTypeInfo | Документация Майкрософт
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
ms.openlocfilehash: 2420713e0adb7f0b7c983243b4021ebbe9b141c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466214"
---
# <a name="example-sqlgettypeinfo-result-set"></a>Пример результирующего набора SQLGetTypeInfo
Приложение вызывает **SQLGetTypeInfo** , чтобы определить, какие типы данных поддерживаются источником данных, и характеристики этих типов данных. В следующих таблицах показан образец результирующего набора, возвращаемого функцией **SQLGetTypeInfo** для источника данных, который поддерживает SQL_CHAR, SQL_LONGVARCHAR, SQL_DECIMAL, SQL_REAL, SQL_DATETIME, SQL_INTERVAL_YEAR и SQL_INTERVAL_DAY_TO_SECOND.  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|типа|SQL_CHAR|255|"'"|"'"|недопустим|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<Null>|SQL_TRUE|  
|десятич|SQL_DECIMAL|28|\<Null>|\<Null>|обеспечивают<br />Измените|SQL_TRUE|  
|Real|SQL_REAL|7|\<Null>|\<Null>|\<Null>|SQL_TRUE|  
|DateTime|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<Null>|SQL_TRUE|  
|"ИНТЕРВАЛ (ГОД) ДО ГОДА"|SQL_INTERVAL_YEAR|9|"'"|"'"|обеспечивают|SQL_TRUE|  
|"INTERVAL DAY () TO ДРОБЬ (5)"|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|обеспечивают|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|ДОСТУПНЫЙ ДЛЯ ПОИСКА|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<Null>|SQL_FALSE|\<Null>|типа|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<Null>|SQL_FALSE|\<Null>|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|десятич|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|Real|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<Null>|SQL_FALSE|\<Null>|DateTime|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<Null>|SQL_FALSE|\<Null>|"ИНТЕРВАЛ (ГОД) ДО ГОДА"|  
|**SQL_INTERVAL_DAY_TO_SECOND**|SQL_FALSE|SQL_PRED_BASIC|\<Null>|SQL_FALSE|\<Null>|"INTERVAL DAY () TO ДРОБЬ (5)"|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<Null>|\<Null>|SQL_CHAR|\<Null>|\<Null>|\<Null>|  
|**SQL_LONGVARCHAR**|\<Null>|\<Null>|SQL_LONGVARCHAR|\<Null>|\<Null>|\<Null>|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<Null>|10|\<Null>|  
|**SQL_REAL**|\<Null>|\<Null>|SQL_REAL|\<Null>|10|\<Null>|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<Null>|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<Null>|9|  
|**SQL_INTERVAL_DAY_TO_SECOND**|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<Null>|9|
