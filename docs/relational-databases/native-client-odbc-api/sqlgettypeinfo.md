---
title: SQLGetTypeInfo | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ebeffb57ccfb6b651dc126f814615322250cd47e
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786312"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает дополнительный столбец USERTYPE в результирующем наборе **SQLGetTypeInfo**. USERTYPE возвращает определение типа данных DB-Library. Этот столбец полезен разработчикам, которые переносят существующие приложения DB-Library в ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассматривает идентификатор как атрибут, а в ODBC он считается типом данных. Чтобы устранить это несоответствие, **SQLGetTypeInfo** возвращает типы данных: **интидентити**, **смаллинтидентити**, **тининтидентити**, **деЦималидентити**и **нумериЦидентити**. AUTO_UNIQUE_VALUE столбца результирующего набора **SQLGetTypeInfo** сообщает значение true для этих типов данных.  
  
 Для типов **varchar**, **nvarchar** и **varbinary**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента по-своему 8000, 4000 и 8000 соответственно для COLUMN_SIZE значения, несмотря на то, что оно фактически не ограничено. Это делается в целях обратной совместимости.  
  
 Для типа данных **XML** драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает SQL_SS_LENGTH_UNLIMITED для COLUMN_SIZE неограниченный размер.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo и параметры, возвращающие табличные значения  
 Тип таблицы для возвращающих табличное значение параметров фактически является мета-типом, т. е. типом, используемым для определения других типов. Поэтому он не должен предоставляться через SQLGetTypeInfo. Для получения метаданных для табличных типов, используемых с возвращающими табличное значение параметрами, приложения должны использовать SQLTables, а не SQLGetTypeInfo.  
  
 Дополнительные сведения о получении метдата для возвращающих табличное значение параметров см. в разделе [атрибуты инструкций, влияющие на возвращающие](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)табличное значение параметры.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Поддержка SQLGetTypeInfo для улучшенных функций даты-времени  
 Сведения о значениях, возвращаемых для типов даты-времени, см. в разделе [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные общие сведения см. в разделе [улучшения &#40;даты и времени&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Поддержка SQLGetTypeInfo для больших определяемых пользователем типов данных среды CLR  
 **SQLGetTypeInfo** поддерживает большие определяемые пользователем типы данных CLR (UDT). Дополнительные сведения см. в разделе [типы больших определяемых пользователем &#40;типов&#41;данных CLR ODBC](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также раздел  
   [функции SQLGetTypeInfo](https://go.microsoft.com/fwlink/?LinkId=59356)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
