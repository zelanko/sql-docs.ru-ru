---
title: Поддержка sql_variant для типов даты и времени | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0cbde879e2b7f215c5044936dfbdacab9196f02d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150830"
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>Поддержка sql_variant для типов даты и времени
  В этом разделе описывается поддержка улучшенной функциональности даты и времени типом `sql_variant`.  
  
 Атрибут столбца SQL_CA_SS_VARIANT_TYPE используется для получения типа C для столбца результатов variant. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] появился дополнительный атрибут, SQL_CA_SS_VARIANT_SQL_TYPE, который устанавливает тип SQL столбца результатов variant в дескрипторе строки реализации (IRD). SQL_CA_SS_VARIANT_SQL_TYPE может также использоваться в дескрипторе параметра реализации (IPD) для указания типа SQL параметра SQL_SS_TIME2 или sql_ss_timestampoffset, имеющего тип SQL_C_BINARY C, привязанный к типу SQL_SS_VARIANT.  
  
 Новые типы SQL_SS_TIME2 и SQL_SS_TIMESTAMPOFFSET задаются SQLColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE может возвращаться SQLGetDescField.  
  
 Для столбцов результата драйвер выполняет преобразование из типа variant в типы даты-времени. Дополнительные сведения см. в разделе [преобразования из SQL в C](datetime-data-type-conversions-from-sql-to-c.md). При привязке к SQL_C_BINARY длина буфера должна быть достаточно большой для размещения структуры, соответствующей типу SQL.  
  
 Для параметров SQL_SS_TIME2 и SQL_SS_TIMESTAMPOFFSET драйвер преобразует значения C в значения `sql_variant`, как описано в приведенной ниже таблице. Если параметр привязан как SQL_C_BINARY, а серверный тип — SQL_SS_VARIANT, то параметр будет рассматриваться как двоичное значение, если только приложение не установило для SQL_CA_SS_VARIANT_SQL_TYPE какой-либо другой тип SQL. В таком случае приоритет имеет SQL_CA_SS_VARIANT_SQL_TYPE; то есть если установлен SQL_CA_SS_VARIANT_SQL_TYPE, он переопределяет поведение по умолчанию — вывод типа SQL для variant из типа C.  
  
|Тип C|Тип сервера|Комментарии|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_WCHAR|nvarchar|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_TINYINT|SMALLINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_STINYINT|SMALLINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SHORT|SMALLINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SSHORT|SMALLINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_USHORT|ssNoversion|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_LONG|ssNoversion|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SLONG|ssNoversion|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_ULONG|BIGINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SBIGINT|BIGINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_FLOAT|REAL|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_DOUBLE|FLOAT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_BIT|bit|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_UTINYINT|TINYINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE не установлен.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Масштаб устанавливается в SQL_DESC_PRECISION ( *DecimalDigits* параметр `SQLBindParameter`).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Масштаб устанавливается в SQL_DESC_PRECISION ( *DecimalDigits* параметр `SQLBindParameter`).|  
|SQL_C_TYPE_DATE|Дата|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_TYPE_TIME|time(0)|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Масштаб устанавливается в SQL_DESC_PRECISION ( *DecimalDigits* параметр `SQLBindParameter`).|  
|SQL_C_NUMERIC|Decimal|Точность устанавливается SQL_DESC_PRECISION ( *ColumnSize* параметр `SQLBindParameter`).<br /><br /> Масштабируемый набор для SQL_DESC_SCALE ( *DecimalDigits* функции SQLBindParameter).|  
|SQL_C_SS_TIME2|time|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
  
## <a name="see-also"></a>См. также  
 [Дата и время улучшения &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  
