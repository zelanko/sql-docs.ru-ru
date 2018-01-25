---
title: "Метаданные параметров и результатов | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: metadata [ODBC]
ms.assetid: 1518e6e5-a6a8-4489-b779-064c5624df53
caps.latest.revision: "27"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 788f1a9835ca2a50274699a6c13701d9bb8ee7ea
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="metadata---parameter-and-result"></a>Метаданные - параметров и результатов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В этом разделе приведено описание того, какие данные возвращаются в полях дескриптора параметра реализации (IPD) и дескриптора строки реализации (IRD) для типов данных даты и времени.  
  
## <a name="information-returned-in-ipd-fields"></a>Информация, возвращаемая в полях IPD  
 В полях IPD происходит возврат следующей информации:  
  
|Тип параметра|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_TYPE|SQL_TYPE_DATE|SQL_SS_TYPE_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime** в IRD, **datetime2** в IPD|**DateTime** в IRD, **datetime2** в IPD|**datetime2**|datetimeoffset|  
|SQL_CA_SS_VARIANT_TYPE|SQL_C_TYPE_DATE|SQL_C_TYPE_BINARY|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_C_TYPE_BINARY|  
|SQL_CA_SS_VARIANT_SQL_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_CA_SS_SERVER_TYPE|Недоступно|Недоступно|SQL_SS_TYPE_SMALLDATETIME|SQL_SS_TYPE_DATETIME|SQL_SS_TYPE_DEFAULT|Недоступно|  
  
 Иногда возникают нарушения непрерывности значений диапазона. Например, в диапазоне 8,10...16 отсутствует 9. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
 **datetime2** возвращается в виде имя типа для **smalldatetime** и **datetime** так, как драйвер использует его как тип данных для передачи всех **SQL_TYPE_TIMESTAMP**  значения на сервер.  
  
 SQL_CA_SS_VARIANT_SQL_TYPE — это новое поле дескриптора. Это поле было добавлено в IPD и IRD для приложений можно указать тип значения, связанные с **sqlvariant** (SQL_SSVARIANT) столбцов и параметров  
  
 SQL_CA_SS_SERVER_TYPE — это новое поле (только для IPD), позволяющее в приложениях управлять способом привязки в качестве SQL_TYPE_TYPETIMESTAMP (или в качестве SQL_SS_VARIANT с типом SQL_C_TYPE_TIMESTAMP языка C) параметров, передаваемых на сервер. Если SQL_DESC_CONCISE_TYPE является SQL_TYPE_TIMESTAMP (или SQL_SS_VARIANT — и типом C — SQL_C_TYPE_TIMESTAMP) при вызове SQLExecute или SQLExecDirect значение SQL_CA_SS_SERVER_TYPE определяет потока табличных данных (TDS) тип значения параметра , как показано ниже:  
  
|Значение SQL_CA_SS_SERVER_TYPE|Допустимые значения для SQL_DESC_PRECISION|Допустимые значения для SQL_DESC_LENGTH|Тип потока табличных данных|  
|----------------------------------------|-------------------------------------------|----------------------------------------|--------------|  
|SQL_SS_TYPE_DEFAULT|0..7|19, 21..27|**datetime2**|  
|SQL_SS_TYPE_SMALLDATETIME|0|19|**smalldatetime**|  
|SQL_SS_TYPE_DATETIME|3|23|**datetime**|  
  
 Значение по умолчанию SQL_CA_SS_SERVER_TYPE равно SQL_SS_TYPE_DEFAULT. Настройки SQL_DESC_PRECISION и SQL_DESC_LENGTH проверяются с учетом значения SQL_CA_SS_SERVER_TYPE, как описано в приведенной выше таблице. Если эта проверка завершается неудачно, то происходит возврат значения SQL_ERROR и в журнал вносится диагностическая запись с кодом SQLSTATE (равным 07006) и сообщением «Нарушение атрибута ограниченного типа данных». Возврат этой ошибки происходит также, если параметру SQL_CA_SS_SERVER_TYPE присвоено значение, отличное от SQL_SS_TYPE DEFAULT, а параметр DESC_CONCISE_TYPE не равен SQL_TYPE_TIMESTAMP. Эти проверки осуществляются при проведении проверки согласованности дескриптора, например, в следующих случаях.  
  
-   Если изменяется значение SQL_DESC_DATA_PTR.  
  
-   Во время подготовки или выполнения (при вызове функций SQLExecute, SQLExecDirect, SQLSetPos или SQLBulkOperations).  
  
-   Отложенное приложение принудительно неотложенную подготовку путем вызова функции SQLPrepare с Подготовка отключена или путем вызова SQLNumResultCols, SQLDescribeCol или SQLDescribeParam для инструкции, которая подготовлена, но не выполняется.  
  
 Если параметр SQL_CA_SS_SERVER_TYPE был установлен с помощью вызова SQLSetDescField, его значение должно быть равно SQL_SS_TYPE_DEFAULT, SQL_SS_TYPE_SMALLDATETIME или SQL_SS_TYPE_DATETIME. В противном случае происходит возврат значения SQL_ERROR, и в журнал вносится диагностическая запись с кодом SQLState (равным HY092) и сообщением «Неверный атрибут или идентификатор параметра».  
  
 Атрибут SQL_CA_SS_SERVER_TYPE можно использовать в приложениях, зависящих от функциональных возможностей, поддерживаемых **datetime** и **smalldatetime**, но не **datetime2**. Например **datetime2** требует использования **dateadd** и **datediif** функций, тогда как **datetime** и  **smalldatetime** также позволяют арифметические операторы. В большинстве приложений необходимость в этом атрибуте отсутствует, поэтому следует избегать его применения.  
  
## <a name="information-returned-in-ird-fields"></a>Информация, возвращаемая в полях IRD  
 В полях IRD возвращаются следующие сведения:  
  
|Тип столбца|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_CONCISE_TYPE|SQL_TYPE_DATE|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_CODE_DATE|0|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|0|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_DISPLAY_SIZE|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SQL_DESC_LENGTH|10|8,10..16|16|2|19, 21..27|26, 28..34|  
|SQL_DESC_LITERAL_PREFIX|‘|‘|‘|‘|‘|‘|  
|SQL_DESC_LITERAL_SUFFIX|‘|‘|‘|‘|‘|‘|  
|SQL_DESC_LOCAL_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_OCTET_LENGTH|6|12|4|8|16|20|  
|SQL_DESC_PRECISION|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SCALE|0|0..7|0|3|0..7|0..7|  
|SQL_DESC_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|SQL_DESC_TYPE|SQL_DATETIME|SQL_SS_TIME2|SQL_DATETIME|SQL_DATETIME|SQL_DATETIME|SQL_SS_TIMESTAMPOFFSET|  
|SQL_DESC_TYPE_NAME|**date**|**time**|**smalldatetime**|**datetime**|**datetime2**|datetimeoffset|  
|SQL_DESC_UNSIGNED|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|SQL_TRUE|  
  
## <a name="see-also"></a>См. также  
 [Метаданные &#40; ODBC &#41;](http://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
  
  
