---
title: Числовые функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e744d3de177197923540fc3101c58dcbb4d3490
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990728"
---
# <a name="numeric-functions"></a>Числовые функции
В следующей таблице описаны числовые функции, которые включены в набор скалярных функций ODBC. Вызывая **SQLGetInfo** с *типом сведений* SQL_NUMERIC_FUNCTIONS, приложение может определить, какие числовые функции поддерживаются драйвером.  
  
 Все числовые функции возвращают значения типа данных SQL_FLOAT за исключением ABS, ROUND, TRUNCATE, SIGN, FLOOR и CEILING, которые возвращают значения того же типа данных, что и входные параметры.  
  
 Аргументами, обозначенными как *numeric_exp* , может быть имя столбца, результат другой скалярной функции или *числовой литера*l, где базовый тип данных может быть представлен как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL или SQL_DOUBLE.  
  
 Аргументами, обозначенными как *float_exp* , может быть имя столбца, результат другой скалярной функции или *числовой литерал*, где базовый тип данных можно представить как SQL_FLOAT.  
  
 Аргументами, обозначенными как *integer_exp* , может быть имя столбца, результат другой скалярной функции или *числовой литерал*, где базовый тип данных может быть представлен как SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER или SQL_BIGINT.  
  
 Скалярные функции CURRENT_DATE, CURRENT_TIME и CURRENT_TIMESTAMP были добавлены в ODBC 3,0 для согласования с SQL-92.  
  
|Компонент|Description|  
|--------------|-----------------|  
|**ABS (** _numeric_exp_ **)** (ODBC 1,0)|Возвращает абсолютное значение *numeric_exp*.|  
|**ACOS (** _float_exp_ **)** (ODBC 1,0)|Возвращает арккосинус *float_exp* в виде угла, выраженного в радианах.|  
|**ASIN (** _float_exp_ **)** (ODBC 1,0)|Возвращает арксинус *float_exp* в виде угла, выраженного в радианах.|  
|**ATAN (** _float_exp_ **)** (ODBC 1,0)|Возвращает арктангенс *float_exp* в виде угла, выраженного в радианах.|  
|**Atan2 (** _float_exp1_, _float_exp2_**)** (ODBC 2,0)|Возвращает арктангенс координат *x* и *y* , заданный с помощью *float_exp1* и *float_exp2*соответственно, в виде угла, выраженного в радианах.|  
|**Ceiling (** _numeric_exp_ **)** (ODBC 1,0)|Возвращает наименьшее целое число, которое больше или равно *numeric_exp*. Возвращаемое значение имеет тот же тип данных, что и входной параметр.|  
|**Cos (** _float_exp_ **)** (ODBC 1,0)|Возвращает косинус *float_exp*, где *float_exp* является углом, выраженным в радианах.|  
|**COT (** _float_exp_ **)** (ODBC 1,0)|Возвращает котангенс *float_exp*, где *float_exp* является углом, выраженным в радианах.|  
|**Градусы (** _numeric_exp_ **)** (ODBC 2,0)|Возвращает число градусов, преобразованное из *numeric_exp* радиан.|  
|**Exp (** _float_exp_ **)** (ODBC 1,0)|Возвращает экспоненциальное значение *float_exp*.|  
|**Floor (** _numeric_exp_ **)** (ODBC 1,0)|Возвращает максимальное целое число, которое меньше или равно *numeric_exp*. Возвращаемое значение имеет тот же тип данных, что и входной параметр.|  
|**Журнал (** _float_exp_ **)** (ODBC 1,0)|Возвращает натуральный логарифм *float_exp*.|  
|**LOG10 (** _float_exp_ **)** (ODBC 2,0)|Возвращает логарифм *float_exp*с основанием 10.|  
|**Mod (** _integer_exp1_, _integer_exp2_**)** (ODBC 1,0)|Возвращает остаток (остаток от деления) *integer_exp1* на *integer_exp2*.|  
|**Pi ()** (ODBC 1,0)|Возвращает постоянное значение PI в виде значения с плавающей запятой.|  
|**Мощность (** _numeric_exp_, _integer_exp_**)** (ODBC 2,0)|Возвращает значение *numeric_exp* в степени *integer_exp*.|  
|**Радианы (** _numeric_exp_ **)** (ODBC 2,0)|Возвращает число радиан, преобразованных из *numeric_exp* градусов.|  
|**Rand (**[*integer_exp*]**)** (ODBC 1,0)|Возвращает случайное значение с плавающей запятой, используя *integer_exp* как необязательное начальное значение.|  
|**Round (** _numeric_exp_, _integer_exp_**)** (ODBC 2,0)|Возвращает *numeric_exp* с округлением до *integer_exp* позиций справа от десятичной запятой. Если *integer_exp* является отрицательным, *numeric_exp* округляется до &#124;*integer_exp*&#124; разрядов слева от десятичной запятой.|  
|**Sign (** _numeric_exp_ **)** (ODBC 1,0)|Возвращает признак знака *numeric_exp*. Если *numeric_exp* меньше нуля, возвращается значение-1. Если *numeric_exp* равно нулю, возвращается значение 0. Если *numeric_exp* больше нуля, возвращается значение 1.|  
|**Sin (** _float_exp_ **)** (ODBC 1,0)|Возвращает синус *float_exp*, где *float_exp* является углом, выраженным в радианах.|  
|**Sqrt (** _float_exp_ **)** (ODBC 1,0)|Возвращает квадратный корень из *float_exp*.|  
|**Tan (** _float_exp_ **)** (ODBC 1,0)|Возвращает тангенс *float_exp*, где *float_exp* является углом, выраженным в радианах.|  
|**Truncate (** _numeric_exp_, _integer_exp_**)** (ODBC 2,0)|Возвращает *numeric_exp* , обрезанные до *integer_exp* разрядов справа от десятичной запятой. Если *integer_exp* является отрицательным, *numeric_exp* усекается до &#124;*integer_exp*&#124; разрядов слева от десятичной запятой.|
