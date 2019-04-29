---
title: SQLProcedureColumns | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 73a6ae0a7209eaef4438aee865f8e887af4ed176
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014296"
---
# <a name="sqlprocedurecolumns"></a>SQLProcedureColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Функция**SQLProcedureColumns** возвращает одну строку, содержащую атрибуты возвращенного значения всех хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Функция**SQLProcedureColumns** возвращает значение SQL_SUCCESS, указывая, существуют ли значения, соответствующие параметрам *CatalogName*, *SchemaName*, *ProcName*и *ColumnName* . Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 Функцию**SQLProcedureColumns** можно выполнить для статического серверного курсора. При попытке выполнить функцию **SQLProcedureColumns** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 В следующей таблице перечислены столбцы, возвращенные результирующим набором, и описывается, как они были расширены для обработки типов данных **udt** и **xml** с помощью драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|SS_UDT_CATALOG_NAME|Возвращает имя каталога, содержащего определяемый пользователем тип.|  
|SS_UDT_SCHEMA_NAME|Возвращает имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Возвращает имя сборки определяемого пользователем типа.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Возвращает имя каталога, в котором определено имя коллекции схем XML. Если обнаружить имя каталога невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Возвращает имя схемы, в которой определено имя коллекции схем XML. Если обнаружить имя схемы невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_NAME|Возвращает имя коллекции схем XML. Если обнаружить имя невозможно, то эта переменная содержит пустую строку.|  
  
## <a name="sqlprocedurecolumns-and-table-valued-parameters"></a>Функция SQLProcedureColumns и возвращающие табличное значение параметры  
 SQLProcedureColumns обрабатывает возвращающие табличные значения параметры так же, как определяемые пользователем типы среды CLR. В строках, возвращенных в возвращающих табличное значение параметрах, столбцы содержат следующие значения.  
  
|Имя столбца|Описание/значение|  
|-----------------|------------------------|  
|DATA_TYPE|SQL_SS_TABLE|  
|TYPE_NAME|Имя табличного типа возвращающего табличное значение параметра.|  
|COLUMN_SIZE|NULL|  
|BUFFER_LENGTH|0|  
|DECIMAL_DIGITS|Число столбцов возвращающего табличное значение параметра.|  
|NUM_PREC_RADIX|NULL|  
|NULLABLE|SQL_NULLABLE|  
|REMARKS|NULL|  
|COLUMN_DEF|NULL. У табличных типов могут отсутствовать значения по умолчанию.|  
|SQL_DATA_TYPE|SQL_SS_TABLE|  
|SQL_DATEIME_SUB|NULL|  
|CHAR_OCTET_LENGTH|NULL|  
|IS_NULLABLE|"YES"|  
|SS_TYPE_CATALOG_NAME|Возвращает имя каталога, содержащего таблицу или определяемый пользователем тип данных CLR.|  
|SS_TYPE_SCHEMA_NAME|Возвращает имя схемы, содержащей таблицу или определяемый пользователем тип среды CLR.|  
  
 Столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME доступны в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях и служат соответственно для возврата каталога и схемы возвращающим табличное значение параметрам. Эти столбцы заполняются для возвращающих табличное значение параметров, а также для определяемых пользователем параметров среды CLR. (Существующие столбцы схем и каталогов для параметров определяемых пользователем типов данных среды CLR этой дополнительной функциональностью не затрагиваются. Они заполняются для поддержания обратной совместимости.)  
  
 В соответствии со спецификацией ODBC столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME располагаются перед каждым, зависящим от драйвера столбцом, добавленным в предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и после всех столбцов, объявленных ODBC.  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLProcedureColumns улучшенных возможностей даты и времени  
 Сведения о значениях, возвращаемых для типов даты-времени, см. в разделе [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLProcedureColumns определяемых пользователем типов больших данных CLR  
 Функция**SQLProcedureColumns** поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedureColumns](https://go.microsoft.com/fwlink/?LinkId=59363)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
