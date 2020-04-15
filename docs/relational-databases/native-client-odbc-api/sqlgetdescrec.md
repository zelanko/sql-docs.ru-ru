---
title: СЗЛГетДесккрек (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 42c8a45bb50e5fda8946cc3819aa4702f5c2fb3f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299564"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этой теме обсуждается функциональность S'LGetDescrec, которая характерна для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] коренных клиентов.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>Функция SQLGetDescRec и возвращающие табличные значения параметры  
 Для получения значений для атрибутов параметров, ценных на стол, и столовых столбцов, можно использовать значения параметров, ценных на таблицу. Параметр *RecNumber,* относящееся к параметру *ParameterNumber,* соблюдаемый в рамках S'LBindParameter.  
  
 Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Для получения более подробной информации о SQL_SOPT_SS_PARAM_FOCUS, [см.](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
 S'LGetDescRec возвращает следующие данные:  
  
|Параметр|Возвращающий табличное значение параметр|Столбцы возвращающих табличные значения параметров и других параметров|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*имя*;|Имя параметра для вызова хранимой процедуры; в противном случае строка длины 0.|Имя столбца возвращающих табличные значения параметров.|  
|*TypePtr*|SQL_DESC_TYPE. Для возвращающих табличные значения параметров — SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*SubTypePtr*|Не определено.|SQL_DESC_DATETIME_INTERVAL_CODE (для записей типа SQL_DATETIME или SQL_INTERVAL).|  
|*ДлинаПтр*|0|SQL_DESC_OCTET_LENGTH|  
|*PrecisionPtr*|0|SQL_DESC_PRECISION|  
|*ScalePtr*|0|SQL_DESC_SCALE|  
|*NullablePtr*|1|SQL_DESC_NULLABLE|  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLGetDescRec улучшенных функций даты и времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*TypePtr*|*SubTypePtr*|*ДлинаПтр*|*PrecisionPtr*|*ScalePtr*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|Дата|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>Поддержка функцией SQLGetDescRec больших определяемых пользователем типов (UDT) среды CLR  
 **S'LGetDesccRec** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [СЗЛГетДескКрек](https://go.microsoft.com/fwlink/?LinkId=80707)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
