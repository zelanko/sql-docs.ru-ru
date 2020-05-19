---
title: SQLProcedureColumns | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 536d8551b82918aae34fa25723c99e8cfad5f1ad
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705884"
---
# <a name="sqlprocedurecolumns"></a>SQLProcedureColumns
  `SQLProcedureColumns`Возвращает одну строку, сообщающую атрибуты возвращаемого значения всех [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимых процедур.  
  
 `SQLProcedureColumns`Возвращает SQL_SUCCESS, существуют ли значения для параметров *CatalogName*, *SchemaName*, *CNAME*или *ColumnName* . Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 Метод `SQLProcedureColumns` может быть выполнен для статического серверного курсора. При попытке выполнить метод `SQLProcedureColumns` для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
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
 SQLProcedureColumns обрабатывает возвращающие табличное значение параметры так же, как и определяемые пользователем типы данных CLR. В строках, возвращенных в возвращающих табличное значение параметрах, столбцы содержат следующие значения.  
  
|Имя столбца|Описание/значение|  
|-----------------|------------------------|  
|DATA_TYPE|SQL_SS_TABLE|  
|TYPE_NAME|Имя табличного типа возвращающего табличное значение параметра.|  
|COLUMN_SIZE|NULL|  
|BUFFER_LENGTH|0|  
|DECIMAL_DIGITS|Число столбцов возвращающего табличное значение параметра.|  
|NUM_PREC_RADIX|NULL|  
|NULLABLE|SQL_NULLABLE|  
|ПРИМЕЧАНИЯ|NULL|  
|COLUMN_DEF|NULL. У табличных типов могут отсутствовать значения по умолчанию.|  
|SQL_DATA_TYPE|SQL_SS_TABLE|  
|SQL_DATEIME_SUB|NULL|  
|CHAR_OCTET_LENGTH|NULL|  
|IS_NULLABLE|"YES"|  
|SS_TYPE_CATALOG_NAME|Возвращает имя каталога, содержащего таблицу или определяемый пользователем тип данных CLR.|  
|SS_TYPE_SCHEMA_NAME|Возвращает имя схемы, содержащей таблицу или определяемый пользователем тип среды CLR.|  
  
 Столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME доступны в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях и служат соответственно для возврата каталога и схемы возвращающим табличное значение параметрам. Эти столбцы заполняются для возвращающих табличное значение параметров, а также для определяемых пользователем параметров среды CLR. (Существующие столбцы схем и каталогов для параметров определяемых пользователем типов данных среды CLR этой дополнительной функциональностью не затрагиваются. Они заполняются для поддержания обратной совместимости.)  
  
 В соответствии со спецификацией ODBC столбцы SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME располагаются перед каждым, зависящим от драйвера столбцом, добавленным в предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и после всех столбцов, объявленных ODBC.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLProcedureColumns улучшенных возможностей даты и времени  
 Сведения о значениях, возвращаемых для типов даты-времени, см. в разделе [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные общие сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLProcedureColumns определяемых пользователем типов больших данных CLR  
 Функция `SQLProcedureColumns` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedureColumns](https://go.microsoft.com/fwlink/?LinkId=59363)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
