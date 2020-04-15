---
title: C Интервальная структура Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02c86ebe24a0e12531e355f95185b01f3089a31b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292156"
---
# <a name="c-interval-structure"></a>Структура Interval (C)
Каждый из типов данных интервала C, перечисленных в разделе [C Data Types,](../../../odbc/reference/appendixes/c-data-types.md) использует одну и ту же структуру для сдерживания интервальных данных. При вызове **S'LFetchFetch,** **S'LFetchScroll**, или **S'LGetData,** драйвер возвращает данные в структуру SQL_INTERVAL_STRUCT, использует значение, указанное приложением для типов данных C (в вызове к **S'LBindCol**, **S'LGetData**, или **S'LBindParameter)** для интерпретации содержимого SQL_INTERVAL_STRUCT, и заполняет *interval_type* поле структуры с значением *enum,* соответствующим типу C. Обратите внимание, что водители не читают *interval_type* поле для определения типа интервала; они извлекают значение поля SQL_DESC_CONCISE_TYPE дескриптора. Когда структура используется для данных параметров, драйвер использует значение, указанное приложением в SQL_DESC_CONCISE_TYPE поле APD, чтобы интерпретировать содержимое SQL_INTERVAL_STRUCT, даже если приложение устанавливает значение *interval_type* поле к другому значению.  
  
 Эта структура определяется следующим образом:  
  
```  
typedef struct tagSQL_INTERVAL_STRUCT  
{  
   SQLINTERVAL interval_type;   
   SQLSMALLINT interval_sign;  
   union {  
         SQL_YEAR_MONTH_STRUCT   year_month;  
         SQL_DAY_SECOND_STRUCT   day_second;  
         } intval;  
} SQL_INTERVAL_STRUCT;  
typedef enum   
{  
   SQL_IS_YEAR = 1,  
   SQL_IS_MONTH = 2,  
   SQL_IS_DAY = 3,  
   SQL_IS_HOUR = 4,  
   SQL_IS_MINUTE = 5,  
   SQL_IS_SECOND = 6,  
   SQL_IS_YEAR_TO_MONTH = 7,  
   SQL_IS_DAY_TO_HOUR = 8,  
   SQL_IS_DAY_TO_MINUTE = 9,  
   SQL_IS_DAY_TO_SECOND = 10,  
   SQL_IS_HOUR_TO_MINUTE = 11,  
   SQL_IS_HOUR_TO_SECOND = 12,  
   SQL_IS_MINUTE_TO_SECOND = 13  
} SQLINTERVAL;  
  
typedef struct tagSQL_YEAR_MONTH  
{  
   SQLUINTEGER year;  
   SQLUINTEGER month;   
} SQL_YEAR_MONTH_STRUCT;  
  
typedef struct tagSQL_DAY_SECOND  
{  
   SQLUINTEGER day;  
   SQLUINTEGER hour;  
   SQLUINTEGER minute;  
   SQLUINTEGER second;  
   SQLUINTEGER fraction;  
} SQL_DAY_SECOND_STRUCT;  
```  
  
 *В interval_type* поле SQL_INTERVAL_STRUCT указывается в заявке, какая структура находится в союзе, а также какие члены структуры имеют отношение. *Поле interval_sign* имеет значение SQL_FALSE, если поле интервала является неподписанным; если это SQL_TRUE, то лидирующая область отрицательна. Значение в самой ведущей области всегда не подписано, независимо от значения *interval_sign.* *Поле interval_sign* действует как знак бита.
