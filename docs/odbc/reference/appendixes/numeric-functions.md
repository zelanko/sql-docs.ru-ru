---
title: Числовые функции Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 03da5b6644e0f7df3dc4e5e16a211cb503023bad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299874"
---
# <a name="numeric-functions"></a>Числовые функции
В следующей таблице описаны числовые функции, включенные в набор функций масштабирования ODBC. Позвонив по **телефону s'LGetInfo** с *информационным типом* SQL_NUMERIC_FUNCTIONS, приложение может определить, какие числовые функции поддерживаются драйвером.  
  
 Все числовые функции возвращают значения типа данных SQL_FLOAT за исключением ABS, ROUND, TRUNCATE, SIGN, FLOOR и CEILING, которые возвращают значения того же типа данных, что и параметры ввода.  
  
 Аргументы, обозначаемые как *numeric_exp,* могут быть названием столбца, результатом другой функции масштабирования или *числового литра*l, где базовый тип данных может быть представлен как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL или SQL_DOUBLE.  
  
 Аргументы, обозначаемые как *float_exp* может быть названием столбца, результатом другой функции масштабирования или *численно-буквального,* где базовый тип данных может быть представлен как SQL_FLOAT.  
  
 Аргументы, обозначаемые как *integer_exp* могут быть названием столбца, результатом другой функции масштабирования или *числового буквара,* где базовый тип данных может быть представлен как SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER или SQL_BIGINT.  
  
 В ODBC 3.0 были добавлены функции CURRENT_DATE, CURRENT_TIME и CURRENT_TIMESTAMP масштабирования, чтобы выровнять его с S'L-92.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|**АБС** _(numeric_exp)_ **)** (ODBC 1.0)|Возвращает абсолютное значение *numeric_exp.*|  
|**ACOS** _(float_exp_ **)** (ODBC 1.0)|Возвращает дугкозин *float_exp* в виде угла, выраженного в радиане.|  
|**АСИН(float_exp** _float_exp_ **)** (ODBC 1.0)|Возвращает дугу *float_exp* как угол, выраженный в радианах.|  
|**АТАН (FLOAT_EXP** _float_exp_ **)** (ODBC 1.0)|Возвращает дуговую *float_exp* float_exp как угол, выраженный в радианах.|  
|**ATAN2** _(float_exp1_, _float_exp2_**)** (ODBC 2.0)|Возвращает дугтанттики координат *x* и *y,* указанные *float_exp1* и *float_exp2,* соответственно, в виде угла, выраженного в радианах.|  
|**ПОТОЛЕТс** _(numeric_exp)_ **)** (ODBC 1.0)|Возвращает наименьший штат больше или равен *numeric_exp.* Значение возврата имеет тот же тип данных, что и параметр ввода.|  
|**COS (float_exp** _float_exp_ **)** (ODBC 1.0)|Возвращает cosine *float_exp*, где *float_exp* угол, выраженный в радианов.|  
|**КОТ(float_exp)** _float_exp_ **)** (ODBC 1.0)|Возвращает cotangent *float_exp*, где *float_exp* угол, выраженный в радианов.|  
|**ГРАДУСОВ** _(numeric_exp)_ **)** (ODBC 2.0)|Возвращает количество степеней, преобразованных из *numeric_exp* радий.|  
|**EXP** _(float_exp)_ **)** (ODBC 1.0)|Возвращает экспоненциальную стоимость *float_exp.*|  
|**Этаж** _(numeric_exp)_ **)** (ODBC 1.0)|Возвращает самый большой штат меньше или равен *numeric_exp.* Значение возврата имеет тот же тип данных, что и параметр ввода.|  
|**ЛОГ (FLOAT_EXP** _float_exp_ **)** (ODBC 1.0)|Возвращает естественный logarithm *float_exp*.|  
|**LOG10** _(float_exp)_ **)** (ODBC 2.0)|Возвращает базу 10 logarithm *float_exp*.|  
|**Мод** _(integer_exp1,_ _integer_exp2)_**)** (ODBC 1.0)|Возвращает оставшуюся часть (модуль) *integer_exp1* разделена *на integer_exp2.*|  
|**PI)** (ODBC 1.0)|Возвращает постоянное значение pi в качестве значения плавающей точки.|  
|**POWER (numeric_exp** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Возвращает ценность *numeric_exp* к силе *integer_exp.*|  
|**РАДИАНС** _(numeric_exp)_ **)** (ODBC 2.0)|Возвращает количество радов, преобразованных с *numeric_exp* градусов.|  
|**RAND (***integer_exp***)** (ODBC 1.0)|Возвращает случайное значение плавающей точки, используя *integer_exp* в качестве дополнительного значения семян.|  
|**ROUND (numeric_exp** _numeric_exp_, _integer_exp)_**)** (ODBC 2.0)|Возвращает *numeric_exp* округлены *к integer_exp* местах право десятичной точки. Если *integer_exp* отрицательный, *numeric_exp* округляется, чтобы &#124;*integer_exp*&#124; места слева от десятичной точки.|  
|**SIGN (numeric_exp** _numeric_exp_ **)** (ODBC 1.0)|Возвращает индикатор знака *numeric_exp.* Если *numeric_exp* меньше нуля, возвращается -1. Если *numeric_exp* равняется нулю, 0 возвращается. Если *numeric_exp* больше нуля, возвращается 1.|  
|**SIN** _(float_exp)_ **)** (ODBC 1.0)|Возвращает синусоиму *float_exp,* где *float_exp* угол, выраженный в радиане.|  
|**СКРТ** _(float_exp)_ **)** (ODBC 1.0)|Возвращает квадратный корень *float_exp*.|  
|**ТАН** _(float_exp)_ **)** (ODBC 1.0)|Возвращает касательную *float_exp,* где *float_exp* является углом, выраженным в радиане.|  
|**TRUNCATE(** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Возвращает *numeric_exp* усеченный, чтобы *integer_exp* местапрямо десятичной точки. Если *integer_exp* отрицательный, *numeric_exp* усечен &#124;*integer_exp*&#124; местах слева от десятичной точки.|
