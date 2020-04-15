---
title: sql_variant поддержка типов дат и времени Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 588fcceb40ea096c549a004c1e2636d0eaf17c6c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291739"
---
# <a name="sql_variant-support-for-date-and-time-types"></a>Поддержка sql_variant для типов даты и времени
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этой теме **описывается,** как sql_variant тип данных поддерживает расширенную функциональность даты и времени.  
  
 Атрибут столбца SQL_CA_SS_VARIANT_TYPE используется для получения типа C для столбца результатов variant. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]В  появился дополнительный атрибут SQL_CA_SS_VARIANT_SQL_TYPE, который устанавливает тип SQL столбца результатов variant в дескрипторе строки реализации (IRD)). SQL_CA_SS_VARIANT_SQL_TYPE также можно использовать в дескрипторе параметра реализации (IPD), чтобы указать тип SQL для параметра SQL_SS_TIME2 или SQL_SS_TIMESTAMPOFFSET, имеющего тип SQL_C_BINARY C, привязанный к типу SQL_SS_VARIANT.  
  
 Новые типы SQL_SS_TIME2 и SQL_SS_TIMESTAMPOFFSET могут быть установлены s'LColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE может быть возвращена s'LGetDescField.  
  
 Для столбцов результата драйвер выполняет преобразование из типа variant в типы даты-времени. Для получения дополнительной [информации см.](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md) При привязке к SQL_C_BINARY длина буфера должна быть достаточно большой, чтобы получить структуру, соответствующую типу S'L.  
  
 Для параметров SQL_SS_TIME2 и SQL_SS_TIMESTAMPOFFSET драйвер преобразует значения C **в sql_variant** значения, как описано в таблице ниже. Если параметр привязан как SQL_C_BINARY, а серверный тип — SQL_SS_VARIANT, то параметр будет рассматриваться как двоичное значение, если только приложение не установило для SQL_CA_SS_VARIANT_SQL_TYPE какой-либо другой тип SQL. В таком случае приоритет имеет SQL_CA_SS_VARIANT_SQL_TYPE; то есть если установлен SQL_CA_SS_VARIANT_SQL_TYPE, он переопределяет поведение по умолчанию — вывод типа SQL для variant из типа C.  
  
|Тип C|Тип сервера|Комментарии|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_WCHAR|nvarchar|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_TINYINT|smallint|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_STINYINT|smallint|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SHORT|smallint|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SSHORT|smallint|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_USHORT|INT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_LONG|INT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SLONG|INT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_ULONG|BIGINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SBIGINT|BIGINT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_FLOAT|real|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_DOUBLE|FLOAT|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_BIT|bit|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_UTINYINT|tinyint|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE не установлен.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Шкала установлена на SQL_DESC_PRECISION (параметр *десятичных диги нот* **S'LBindParameter).**|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Шкала установлена на SQL_DESC_PRECISION (параметр *десятичных диги нот* **S'LBindParameter).**|  
|SQL_C_TYPE_DATE|Дата|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_TYPE_TIME|time(0)|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Шкала установлена на SQL_DESC_PRECISION (параметр *десятичных диги нот* **S'LBindParameter).**|  
|SQL_C_NUMERIC|Decimal|Точность устанавливается на SQL_DESC_PRECISION (параметр *ColumnSize* **S'LBindParameter).**<br /><br /> Шкала установлена на SQL_DESC_SCALE (параметр *десятичных диги,* параметр S'LBindParameter).|  
|SQL_C_SS_TIME2|time|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|Значение SQL_CA_SS_VARIANT_SQL_TYPE не учитывается.|  
  
## <a name="see-also"></a>См. также:  
 [Улучшение даты и времени &#40;&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
