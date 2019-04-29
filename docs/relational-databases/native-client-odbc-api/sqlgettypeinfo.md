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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e6d813848a45326ee9a74ea38616ceef9dd02cd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63015686"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Отчеты драйвер ODBC для собственного клиента, дополнительный столбец USERTYPE в результирующем наборе **SQLGetTypeInfo**. USERTYPE возвращает определение типа данных DB-Library. Этот столбец полезен разработчикам, которые переносят существующие приложения DB-Library в ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассматривает идентификатор как атрибут, а в ODBC он считается типом данных. Чтобы устранить это несоответствие **SQLGetTypeInfo** возвращает типы данных: **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity**, и **numericidentity**. **SQLGetTypeInfo** столбец результирующего набора AUTO_UNIQUE_VALUE сообщает значение TRUE для типов данных.  
  
 Для **varchar**, **nvarchar** и **varbinary**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] продолжает сообщать 8000, 4000 и 8000 соответственно для COLUMN_SIZE драйвер ODBC собственного клиента значение, несмотря на то, что фактически неограничен. Это делается в целях обратной совместимости.  
  
 Для **xml** тип данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента сообщает значение SQL_SS_LENGTH_UNLIMITED для COLUMN_SIZE для обозначения неограниченного размера.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo и параметры, возвращающие табличные значения  
 Табличный тип для возвращающих табличные значения параметров является фактически мета тип-, тип, используемый для определения других типов. Таким образом его не нужно предоставлять через SQLGetTypeInfo. Приложения должны использовать SQLTables, а не SQLGetTypeInfo, для получения метаданных для табличных типов, при использовании возвращающих табличные значения параметров.  
  
 Дополнительные сведения о получении метаданных для возвращающих табличные значения параметров, см. в разделе [инструкции атрибуты, что параметры Affect Table-Valued](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Поддержка SQLGetTypeInfo для улучшенных функций даты-времени  
 Сведения о значениях, возвращаемых для типов даты-времени, см. в разделе [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Поддержка SQLGetTypeInfo для больших определяемых пользователем типов данных среды CLR  
 **SQLGetTypeInfo** поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLGetTypeInfo](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
