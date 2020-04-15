---
title: Идентификаторы и дескрипторы типа данных Документы Майкрософт
ms.custom: ''
ms.date: 02/02/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f65bc86213f99112daf17c67a4ca522490d32149
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284487"
---
# <a name="data-type-identifiers-and-descriptors"></a>Идентификаторы и дескрипторы типа данных
Типы данных, перечисленные в разделах [типов данных и](../../../odbc/reference/appendixes/sql-data-types.md) [C типов C,](../../../odbc/reference/appendixes/c-data-types.md) ранее в этом приложении, являются «краткими» типами данных: каждый идентификатор относится к одному типу данных. Существует один-к-одному корреспонденция между идентификатором и типом данных. Дескрипторы, однако, не во всех случаях используют одно значение для определения типов данных. В некоторых случаях они используют "многословный" тип данных и тип подкода. Для всех типов данных, за исключением времени даты и типа интервальных данных, идентификатор многословного типа совпадает с идентификатором краткого типа, а значение в SQL_DESC_DATETIME_INTERVAL_CODE равно 0. Однако для типов данных о дате и интервалах в SQL_DESC_TYPE хранится многословный тип (SQL_DATETIME или SQL_INTERVAL), в SQL_DESC_CONCISE_TYPE хранится краткий тип, а подкод для каждого краткого типа хранится в SQL_DESC_DATETIME_INTERVAL_CODE. Установка одного из этих полей влияет на другие. Для получения более подробной информации об этих полях можно ознакомиться с описанием функции [S'LSetDescField.](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 При установке поля SQL_DESC_TYPE или SQL_DESC_CONCISE_TYPE для некоторых типов данных SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION и SQL_DESC_SCALE поля автоматически устанавливаются значения по умолчанию, применимые к типу данных. Для получения более подробной информаци SQL_DESC_TYPEи, см. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) Если какой-либо из наборов значений по умолчанию не подходит, приложение должно четко установить поле дескриптора через вызов в **S'LSetDescField.**  
  
 В следующей таблице показан идентификатор краткого типа, идентификатор многословного типа и подкод типа для каждого времени даты и идентификатора типа C'L и C. Как указывается в этой таблице, для типов данных даты и интервалов SQL_DESC_TYPE и SQL_DESC_DATETIME_INTERVAL_CODE поля имеют одинаковые константы проявляется как для типов данных S'L (в дескрипторах реализации), так и для типов данных C (в дескрипторах приложений).  
  
|Краткий тип S'L|Краткий тип C|Тип verbose|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
|SQL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
