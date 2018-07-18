---
title: Структура C интервал | Документы Microsoft
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
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f3a2c8f0e3ad967b3c0b7b02255774c2603a1b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906718"
---
# <a name="c-interval-structure"></a>Структура интервала C
Каждый из типов данных C интервал перечисленные в [типы данных C](../../../odbc/reference/appendixes/c-data-types.md) раздел использует ту же структуру для хранения данных интервала. Когда **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** является именем, драйвер возвращает данные в структуру SQL_INTERVAL_STRUCT, используется значение, указанное в параметре приложение для типов данных C (в вызове **SQLBindCol**, **SQLGetData**, или **SQLBindParameter**) интерпретировать содержимое SQL_INTERVAL_STRUCT и заполняет *interval_type* поля структуры с *перечисления* значение, соответствующее типу C. Обратите внимание, что драйверы не читают *interval_type* поле, чтобы определить тип интервала; они извлекают значения поля дескриптора SQL_DESC_CONCISE_TYPE. При использовании структуры данных параметра, драйвер использует значение, указанное для приложения в поле SQL_DESC_CONCISE_TYPE в APD интерпретировать содержимое SQL_INTERVAL_STRUCT, даже если приложение устанавливает значение  *interval_type* поле другое значение.  
  
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
  
 *Interval_type* поле SQL_INTERVAL_STRUCT указывает приложению, какая структура удерживается в объединении и также относятся какие элементы структуры. *Interval_sign* поле имеет значение SQL_FALSE, если поле интервала не подписан; если его значение равно SQL_TRUE, начальные поля является отрицательным. Значение в начале само поле всегда равно без знака, независимо от значения *interval_sign*. *Interval_sign* поле действует как бит знака.
