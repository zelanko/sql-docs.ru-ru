---
title: Метаданные параметров и результатов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b4e7650f6b36ddbfb8c06ebe6c9f776cfee5ea0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63032325"
---
# <a name="parameter-and-result-metadata"></a>Метаданные параметров и результатов
  В этом разделе приведено описание того, какие данные возвращаются в полях дескриптора параметра реализации (IPD) и дескриптора строки реализации (IRD) для типов данных даты и времени.  
  
## <a name="information-returned-in-ipd-fields"></a>Информация, возвращаемая в полях IPD  
 В полях IPD происходит возврат следующей информации:  
  
|Тип параметра|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|Данные типа `smalldatetime` в IRD, данные типа `datetime2` в IPD|Данные типа `datetime` в IRD, данные типа `datetime2` в IPD|`datetime2`|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|Н/Д|Н/Д|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|Н/Д|  
  
 Иногда возникают нарушения непрерывности значений диапазона. Например, в диапазоне 8,10...16 отсутствует 9. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
 Значение `datetime2` возвращается в качестве имени типа для `smalldatetime` и `datetime`, так как драйвер использует его как обычный тип для передачи всех значений `SQL_TYPE_TIMESTAMP` на сервер.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE — это новое поле дескриптора. Это поле было добавлено к полям IPD и IRD, чтобы в приложениях можно было указать тип значения, связанного с `sqlvariant` (SQL_SSVARIANT).  
  
 SQL_CA_SS_SERVER_TYPE — это новое поле (только для IPD), позволяющее в приложениях управлять способом привязки в качестве SQL_TYPE_TYPETIMESTAMP (или в качестве SQL_SS_VARIANT с типом SQL_C_TYPE_TIMESTAMP языка C) параметров, передаваемых на сервер. Если SQL_DESC_CONCISE_TYPE имеет SQL_TYPE_TIMESTAMP (или SQL_SS_VARIANT и тип C SQL_C_TYPE_TIMESTAMP) при вызове SQLExecute или SQLExecDirect, значение SQL_CA_SS_SERVER_TYPE определяет тип потока табличных данных (TDS) для значения параметра следующим образом:  
  
|Значение SQL_CA_SS_SERVER_TYPE|Допустимые значения для SQL_DESC_PRECISION|Допустимые значения для SQL_DESC_LENGTH|Тип потока табличных данных|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|`datetime2`|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|`smalldatetime`|  
|SQL_SS_TYPE_DATETIME|3|23|`datetime`|  
  
 Значение по умолчанию SQL_CA_SS_SERVER_TYPE равно SQL_SS_TYPE_DEFAULT. Настройки SQL_DESC_PRECISION и SQL_DESC_LENGTH проверяются с учетом значения SQL_CA_SS_SERVER_TYPE, как описано в приведенной выше таблице. Если эта проверка завершается неудачно, то происходит возврат значения SQL_ERROR и в журнал вносится диагностическая запись с кодом SQLSTATE (равным 07006) и сообщением «Нарушение атрибута ограниченного типа данных». Возврат этой ошибки происходит также, если параметру SQL_CA_SS_SERVER_TYPE присвоено значение, отличное от SQL_SS_TYPE DEFAULT, а параметр DESC_CONCISE_TYPE не равен SQL_TYPE_TIMESTAMP. Эти проверки осуществляются при проведении проверки согласованности дескриптора, например, в следующих случаях.  
  
-   Если изменяется значение SQL_DESC_DATA_PTR.  
  
-   Во время подготовки или выполнения (при вызове функций SQLExecute, SQLExecDirect, SQLSetPos или SQLBulkOperations).  
  
-   Когда приложение принудительно вызывает неотложенную подготовку путем вызова SQLPrepare с отключенной подготовительной подготовкой или путем вызова SQLNumResultCols, SQLDescribeCol или SQLDescribeParam для инструкции, которая подготовлена, но не выполняется.  
  
 Если SQL_CA_SS_SERVER_TYPE задается вызовом SQLSetDescField, его значение должно быть SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME или SQL_SS_TYPE_DATETIME. В противном случае происходит возврат значения SQL_ERROR, и в журнал вносится диагностическая запись с кодом SQLState (равным HY092) и сообщением «Неверный атрибут или идентификатор параметра».  
  
 Атрибут SQL_CA_SS_SERVER_TYPE можно использовать в приложениях, зависящих от функциональных возможностей, поддерживаемых типами данных `datetime` и `smalldatetime`, но не `datetime2`. `datetime2` Например, необходимо использовать функции `dateadd` и **датедииф** , а также `datetime` и `smalldatetime` разрешить арифметические операторы. В большинстве приложений необходимость в этом атрибуте отсутствует, поэтому следует избегать его применения.  
  
## <a name="information-returned-in-ird-fields"></a>Информация, возвращаемая в полях IRD  
 В полях IRD возвращаются следующие сведения:  
  
|Тип столбца|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8, 10.16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8, 10.16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8, 10.16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|'|'|'|'|'|'|  
|SQL_DESC_LITERAL_SUFFIX|'|'|'|'|'|'|  
|SQL_DESC_LOCAL_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|`date`|`time`|`smalldatetime`|`datetime`|`datetime2`|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>См. также  
 [Метаданные &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
  
  
