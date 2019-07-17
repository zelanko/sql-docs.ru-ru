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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019055"
---
# <a name="data-type-identifiers-and-descriptors"></a>Идентификаторы и дескрипторы типа данных
Типы данных перечислены в [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) и [типы данных C](../../../odbc/reference/appendixes/c-data-types.md) приведенными ранее в этом приложении являются типами «краткое» данных: Каждый идентификатор ссылается на один тип данных. Имеется однозначное соответствие между идентификатором и типом данных. Дескрипторы, однако сделать не в всегда использовать одно значение для идентификации типов данных. В некоторых случаях они используют, типом данных «verbose» и тип дополнительный код. Для всех типов данных, за исключением типов данных даты и времени и интервал идентификатор подробного совпадает со значением идентификатора тип сокращения, и значение SQL_DESC_DATETIME_INTERVAL_CODE равно 0. Для типов данных даты и времени и интервал тем не менее, типом verbose (SQL_DATETIME или SQL_INTERVAL) хранится в SQL_DESC_TYPE тип сокращения хранится в SQL_DESC_CONCISE_TYPE и дополнительный код для каждого краткого типа хранятся в SQL_DESC_DATETIME_INTERVAL_CODE. Настройка одного из этих полей влияет на остальные. Дополнительные сведения об этих полях см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.  
  
 Если поле SQL_DESC_TYPE или SQL_DESC_CONCISE_TYPE имеет значение для некоторых типов данных, поля SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION и SQL_DESC_SCALE автоматически устанавливаются значения по умолчанию, где это применимо для данных тип. Дополнительные сведения см. в описании поля SQL_DESC_TYPE в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Если какая-либо набора значений по умолчанию не подходит, приложение должно явным образом задать поля дескриптора посредством вызова **SQLSetDescField**.  
  
 Следующая таблица показывает тип сокращения идентификатор, идентификатор подробного типа и дополнительный код типа для каждого типа datetime и интервал SQL и идентификатор типа C. Как показано в этой таблице, для типов данных даты и времени и интервал, поля SQL_DESC_TYPE и SQL_DESC_DATETIME_INTERVAL_CODE имеют же констант манифеста, как для типов данных SQL (в дескрипторах реализация), так и для типов данных C (в приложении дескрипторы).  
  
|Тип сокращения SQL|Тип сокращения C|Подробный тип|DATETIME_INTERVAL_CODE|  
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
