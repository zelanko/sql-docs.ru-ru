---
title: СЗЛГетТипИнфо (ru) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81ba57c6e66f156f13055ff5ec941fa8f0c86381
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298456"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC сообщает о дополнительной колонке USERTYPE в итоговом наборе **S'LGetTypeInfo.** USERTYPE возвращает определение типа данных DB-Library. Этот столбец полезен разработчикам, которые переносят существующие приложения DB-Library в ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассматривает идентификатор как атрибут, а в ODBC он считается типом данных. Чтобы устранить это несоответствие, **S'LGetTypeInfo** возвращает типы данных: **intidentity,** **smallintidentity,** **tinyintidentity,** **десятиличность,** и **числовая идентичность.** Столбец набора результатов **s'LGetTypeInfo** AUTO_UNIQUE_VALUE сообщает значение TRUE для этих типов данных.  
  
 Для **varchar**, **nvarchar** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varbinary**, водитель Native Client ODBC продолжает сообщать 8000, 4000 и 8000 соответственно для COLUMN_SIZE значения, даже если это на самом деле неограниченное. Это делается в целях обратной совместимости.  
  
 Для типа данных **xml** драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC сообщает, SQL_SS_LENGTH_UNLIMITED для COLUMN_SIZE обозначают неограниченный размер.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo и параметры, возвращающие табличные значения  
 Тип таблицы для параметров, оцениваемых таблицей, фактически является мета-типом, т.е. типом, используемым для определения других типов. Таким образом, он не должен быть разоблачен через S'LGetTypeInfo. Для извлечения метаданных для типов таблиц, используемых с параметрами, ценных на стол, приложения должны использовать s-LTables, а не S'LGetTypeInfo.  
  
 Для получения дополнительной информации о получении метданных для параметров, ценных на таблицу, см. [Атрибуты оператора, влияющие на параметры, оцениваемые таблицей.](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Поддержка SQLGetTypeInfo для улучшенных функций даты-времени  
 Сведения о значениях, возвращаемых для типов даты-времени, см. в разделе [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Для получения более подробной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Поддержка SQLGetTypeInfo для больших определяемых пользователем типов данных среды CLR  
 **SLGetTypeInfo** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LGetTypeInfo](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
