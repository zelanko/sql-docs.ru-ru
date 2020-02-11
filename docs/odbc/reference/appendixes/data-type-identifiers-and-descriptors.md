---
title: Идентификаторы и дескрипторы типов данных | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 748f2452d20b618ae0011e2e1ac4e24af098ac06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019055"
---
# <a name="data-type-identifiers-and-descriptors"></a>Идентификаторы и дескрипторы типа данных
Типы данных, перечисленные в разделах " [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) " и " [типы данных C](../../../odbc/reference/appendixes/c-data-types.md) ", приведенных выше в этом приложении, являются "лаконичными" типами данных: каждый идентификатор ссылается на один тип данных. Между идентификатором и типом данных существует соответствие "один к одному". Однако дескрипторы не во всех случаях используют одно значение для обнаружения типов данных. В некоторых случаях они используют тип данных "verbose" и код типа. Для всех типов данных, кроме типов данных DateTime и Interval, идентификатор подробного типа совпадает с идентификатором краткого типа, а значение в SQL_DESC_DATETIME_INTERVAL_CODE равно 0. Однако для типов данных DateTime и Interval тип Verbose (SQL_DATETIME или SQL_INTERVAL) хранится в SQL_DESC_TYPE, а сокращенный тип хранится в SQL_DESC_CONCISE_TYPE, а код для каждого краткого типа хранится в SQL_DESC_DATETIME_INTERVAL_CODE. Установка одного из этих полей влияет на другие. Дополнительные сведения об этих полях см. в описании функции [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) .  
  
 Если поле SQL_DESC_TYPE или SQL_DESC_CONCISE_TYPE задано для некоторых типов данных, поля SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION и SQL_DESC_SCALE автоматически устанавливаются в значения по умолчанию, как применимо к данным. Тип. Дополнительные сведения см. в описании поля SQL_DESC_TYPE в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Если какой-либо из установленных значений по умолчанию не подходит, приложение должно явно задать поле дескриптора с помощью вызова **SQLSetDescField**.  
  
 В следующей таблице показан идентификатор краткого типа, подробный идентификатор типа и подкод типа для каждого идентификатора типа DateTime и интервала типов SQL и C. Как показано в этой таблице, для типов данных DateTime и Interval поля SQL_DESC_TYPE и SQL_DESC_DATETIME_INTERVAL_CODE имеют одинаковые константы манифеста как для типов данных SQL (в дескрипторах реализации), так и для типов данных C (в приложении дескрипторы).  
  
|Тип SQL "Краткая"|Сокращенный тип C|Подробный тип|DATETIME_INTERVAL_CODE|  
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
