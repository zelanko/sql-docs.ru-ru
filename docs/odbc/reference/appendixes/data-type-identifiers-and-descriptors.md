---
title: "Идентификаторы и дескрипторы типа | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 93b813632c3a281e1ae0ba90e95545e28d07ed09
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-identifiers-and-descriptors"></a>Идентификаторы типа данных и дескрипторов
Типы данных перечислены в [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) и [типы данных C](../../../odbc/reference/appendixes/c-data-types.md) разделы данного приложения — это типы данных «быстрый»: каждый идентификатор ссылается на один тип данных. Нет однозначного соответствия между идентификатор и тип данных. Дескрипторы, однако сделать не в всегда использовать одно значение для идентификации типов данных. В некоторых случаях они используют тип данных «verbose» и дополнительный код типа. Для всех типов данных, за исключением типов данных даты и времени и интервала идентификатор типа verbose совпадает со значением идентификатора четкими типа, и значение SQL_DESC_DATETIME_INTERVAL_CODE равно 0. Для типов данных даты и времени и интервал тем не менее, типом verbose (SQL_DATETIME или SQL_INTERVAL) хранится в SQL_DESC_TYPE четкими тип хранится в SQL_DESC_CONCISE_TYPE и дополнительный код для каждого типа четкими хранится в SQL_DESC_DATETIME_INTERVAL_CODE. Настройка одного из этих полей влияет на остальные. Дополнительные сведения об этих полях см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.  
  
 Если поле SQL_DESC_TYPE или SQL_DESC_CONCISE_TYPE задан для некоторых типов данных, поля SQL_DESC_DATETIME_INTERVAL_PRECISION, SQL_DESC_LENGTH, SQL_DESC_PRECISION и SQL_DESC_SCALE автоматически устанавливаются значения по умолчанию, как это требуется для данных тип. Дополнительные сведения см. в описании поле SQL_DESC_TYPE в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Если любой из значения по умолчанию не подходит, приложение должно явно задать поля дескриптора посредством вызова **SQLSetDescField**.  
  
 Следующая таблица показывает четкими тип идентификатора, идентификатора типа verbose и дополнительный код типа для каждого типа datetime и интервал SQL и идентификатор типа C. Как этой таблице, для типов данных даты и времени и интервала SQL_DESC_TYPE и SQL_DESC_DATETIME_INTERVAL_CODE поля имеют одинаковые константы манифеста для типов данных SQL (в реализации дескрипторы) и типы данных C (в приложении дескрипторы).  
  
|Краткие тип SQL|Краткие тип C|Подробный тип|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
QL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
QL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
