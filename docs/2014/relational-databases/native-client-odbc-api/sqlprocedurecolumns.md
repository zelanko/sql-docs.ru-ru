---
title: SQLProcedureColumns | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
caps.latest.revision: 50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b693d06e42f0fc5d2815b188826b21f5d89cae7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428393"
---
# <a name="sqlprocedurecolumns"></a>SQLProcedureColumns
  `SQLProcedureColumns` Возвращает одну строку атрибуты возвращенного значения всех [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимых процедур.  
  
 `SQLProcedureColumns` Возвращает значение SQL_SUCCESS независимо от наличия значения существуют для *CatalogName*, *SchemaName*, *ProcName*, или *ColumnName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 Метод `SQLProcedureColumns` может быть выполнен для статического серверного курсора. При попытке выполнить метод `SQLProcedureColumns` для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 В следующей таблице перечислены столбцы, возвращенные результирующим набором, и как они были расширены для обработки **определяемого пользователем типа** и **xml** типы данных через [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента:  
  
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
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLProcedureColumns улучшенных возможностей даты и времени  
 Для значений, возвращаемых для типов даты и времени, см. в разделе [метаданные каталога](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLProcedureColumns определяемых пользователем типов больших данных CLR  
 Функция `SQLProcedureColumns` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedureColumns](http://go.microsoft.com/fwlink/?LinkId=59363)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
