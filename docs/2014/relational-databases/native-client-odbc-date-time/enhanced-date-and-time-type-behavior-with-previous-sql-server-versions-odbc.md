---
title: Улучшение типы даты и времени введите поведение с предыдущими версиями SQL Server (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], enhanced behavior with earlier SQL Server versions
ms.assetid: cd4e137f-dc5e-4df7-bc95-51fe18c587e0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44ac9cecce81f7873ca5ef42ba414bd4528e05b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63140630"
---
# <a name="enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc"></a>Улучшенная работа типа даты-времени с предыдущими версиями SQL Server (ODBC)
  В этом разделе описывается ожидаемое поведение клиентских приложений, использующих улучшенные функции даты и времени, которые подключаются к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версий более ранних, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], а также в случаях, когда клиентское приложение использует компоненты доступа к данным MDAC, Windows DAC или собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] для отправки команд на сервер, поддерживающий улучшенные функции даты и времени.  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиентские приложения, скомпилированные с помощью собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], распознают новые типы даты и времени, как столбцы nvarchar. Содержимое этих столбцов является представлением литералов, как описано в разделе «форматы данных: Строки и литералы» раздела [поддержка типов данных ODBC Дата и время улучшениях](data-type-support-for-odbc-date-and-time-improvements.md). Размер столбца равен максимальной длине литерала для долей секунды, указываемых с заданной для столбца точностью.  
  
 API-интерфейсы каталога возвращают метаданные, согласующиеся с кодом типа данных низкого уровня, полученного клиентом (например, nvarchar) и со связанным представлением низкого уровня (например, с соответствующим форматом литерала). Тем не менее, будет возвращено реальное имя типа данных [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 Инструкция метаданные, возвращаемые функциями SQLDescribeCol, SQLDescribeParam, SQGetDescField и SQLColAttribute возвращают метаданные, которая согласуется с типом низкого уровня во всех отношениях, включая имя типа. Примером такого типа низкого уровня является `nvarchar`.  
  
 При запуске приложения клиента нижнего уровня на [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) сервера, на какие изменения схемы для даты и времени были внесены типов, ожидаемое поведение выглядит следующим образом:  
  
|Тип SQL Server 2005|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) Тип|Клиентский тип ODBC|Преобразование результата (из SQL в C)|Преобразование параметров (из C в SQL)|  
|--------------------------|----------------------------------------------|----------------------|------------------------------------|---------------------------------------|  
|DateTime|Дата|SQL_C_TYPE_DATE|OK|ОК (1)|  
|||SQL_C_TYPE_TIMESTAMP|Поля времени устанавливаются в нули.|OK (2)<br /><br /> Завершается ошибкой, если значение поля времени не равно нулю. Работает с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(0)|SQL_C_TYPE_TIME|OK|ОК (1)|  
|||SQL_C_TYPE_TIMESTAMP|Поля даты устанавливаются в текущую дату.|OK (2)<br /><br /> Дата пропускается. Ошибка, если доли секунды не равны нулю. Работает с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(7)|SQL_C_TIME|Сбой — недопустимый литерал времени.|ОК (1)|  
|||SQL_C_TYPE_TIMESTAMP|Сбой — недопустимый литерал времени.|ОК (1)|  
||Datetime2(3)|SQL_C_TYPE_TIMESTAMP|OK|ОК (1)|  
||datetime2(7)|SQL_C_TYPE_TIMESTAMP|OK|Значение округляется до 1/300 секунды при преобразовании на клиенте.|  
|Smalldatetime|Дата|SQL_C_TYPE_DATE|OK|OK|  
|||SQL_C_TYPE_TIMESTAMP|Поля времени устанавливаются в нули.|OK (2)<br /><br /> Завершается ошибкой, если значение поля времени не равно нулю. Работает с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(0)|SQL_C_TYPE_TIME|OK|OK|  
|||SQL_C_TYPE_TIMESTAMP|Поля даты устанавливаются в текущую дату.|OK (2)<br /><br /> Дата пропускается. Ошибка, если доли секунды не равны нулю.<br /><br /> Работает с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Datetime2(0)|SQL_C_TYPE_TIMESTAMP|OK|OK|  
  
## <a name="key-to-symbols"></a>Расшифровка символов  
  
|Символ|Значение|  
|------------|-------------|  
|1|Если код работал в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], то он должен работать и с последующими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|2|У приложения, работавшего с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], могут возникать ошибки с более поздними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 Обратите внимание, что рассматриваются только типичные изменения схемы. Ниже приводятся типичные изменения.  
  
-   Использование нового типа, когда логически приложению необходимо только значение даты или времени. Однако приложение было вынуждено использовать типы datetime или smalldatetime из-за отсутствия отдельных типов для даты и времени.  
  
-   Использование нового типа для получения долей секунд c более высокой точностью.  
  
-   Переключение на тип datetime2, поскольку это предпочтительный тип для данных даты и времени.  
  
### <a name="column-metadata-returned-by-sqlcolumns-sqlprocedurecolumns-and-sqlspecialcolumns"></a>Метаданные столбцов, возвращаемые SQLColumns, SQLProcedureColumns и SQLSpecialColumns  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_WVARCHAR|SQL_WVARCHAR|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|COLUMN_SIZE|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|BUFFER_LENGTH|20|16, 20..32|16|16|38, 42..54|52, 56..68|  
|DECIMAL_DIGITS|NULL|NULL|0|3|NULL|NULL|  
|SQL_DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_DATETIME|SQL_DATETIME|SQL_WVARCHAR|SQL_WVARCHAR|  
|SQL_DATETIME_SUB|NULL|NULL|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|NULL|NULL|  
|CHAR_OCTET_LENGTH|NULL|NULL|NULL|NULL|NULL|NULL|  
|SS_DATA_TYPE|0|0|111|111|0|0|  
  
 SQLSpecialColumns не возвращает SQL_DATA_TYPE, SQL_DATETIME_SUB, CHAR_OCTET_LENGTH или SS_DATA_TYPE.  
  
### <a name="data-type-metadata-returned-by-sqlgettypeinfo"></a>Метаданные типа данных, возвращенные SQLGetTypeInfo  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_WVARCHAR|SQL_WVARCHAR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|  
|CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|AUTO_UNIQUE_VALUE|NULL|NULL|NULL|NULL|NULL|NULL|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|0|3|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|0|3|NULL|NULL|  
|SQL_DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_DATETIME|SQL_DATETIME|SQL_WVARCHAR|SQL_WVARCHAR|  
|SQL_DATETIME_SUB|NULL|NULL|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|NULL|NULL|  
|NUM_PREC_RADIX|NULL|NULL|NULL|NULL|NULL|NULL|  
|INTERVAL_PRECISION|NULL|NULL|NULL|NULL|NULL|NULL|  
|USERTYPE|0|0|12|22|0|0|  
  
## <a name="down-level-server-behavior"></a>Работа сервера низкого уровня  
 При соединении с экземпляром сервера версии более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], любые попытки использовать новые серверные типы или связанные с ними коды метаданных и поля дескрипторов приводят к возврату ошибки SQL_ERROR. Будет сформирована диагностическая запись с ошибкой SQLSTATE HY004 и сообщением «Недопустимый тип данных SQL для версии сервера при соединении» или с ошибкой 07006 и сообщением «Нарушение атрибута ограниченного типа данных».  
  
## <a name="see-also"></a>См. также  
 [Дата и время улучшения &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  
