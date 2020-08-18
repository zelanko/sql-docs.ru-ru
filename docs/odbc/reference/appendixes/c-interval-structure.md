---
description: Структура Interval (C)
title: Структура интервала C | Документация Майкрософт
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
ms.openlocfilehash: 89962558fdbd6f0de5b5e030fe504669d51c40be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411210"
---
# <a name="c-interval-structure"></a>Структура Interval (C)
Каждый из типов данных интервала C, перечисленных в разделе [типы данных c](../../../odbc/reference/appendixes/c-data-types.md) , использует ту же структуру для хранения данных интервала. При вызове **SQLFetch**, **SQLFetchScroll**или **SQLGetData** драйвер возвращает данные в структуру SQL_INTERVAL_STRUCT, использует значение, заданное приложением для типов данных C (в вызове **SQLBindCol**, **SQLGetData**или **SQLBindParameter**) для интерпретации содержимого SQL_INTERVAL_STRUCT, и заполняет поле *interval_type* структуры значением *перечисления* , соответствующим типу C. Обратите внимание, что драйверы не считывают поле *interval_type* , чтобы определить тип интервала. они получают значение поля дескриптора SQL_DESC_CONCISE_TYPE. Если структура используется для данных параметров, драйвер использует значение, заданное приложением в поле SQL_DESC_CONCISE_TYPE APD для интерпретации содержимого SQL_INTERVAL_STRUCT, даже если приложение устанавливает значение поля *interval_type* в другое значение.  
  
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
  
 *Interval_type* поле SQL_INTERVAL_STRUCT указывает приложению, какая структура удерживается в объединении, а также какие элементы структуры являются релевантными. Поле *interval_sign* имеет значение SQL_FALSE, если начальное поле интервала не подписано; Если это SQL_TRUE, то начальное поле будет отрицательным. Значение в самом начальном поле всегда беззнаковое, независимо от значения *interval_sign*. *Interval_sign* поле действует как бит знака.
