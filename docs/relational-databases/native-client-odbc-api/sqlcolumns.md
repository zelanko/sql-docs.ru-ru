---
title: SQLColumns | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
caps.latest.revision: 62
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f56b3e1b80687692293998b0b7b12daf9af7a330
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416063"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumns** возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName*, *TableName*, или *ColumnName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
> [!NOTE]  
>  Для типов больших значений все параметры длины будут возвращены со значением SQL_SS_LENGTH_UNLIMITED.  
  
 **SQLColumns** может быть выполнена для статического серверного курсора. При попытке выполнить **SQLColumns** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя для *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
 Для ODBC 2. *x* приложений не с помощью подстановочных знаков в *TableName*, **SQLColumns** возвращает сведения обо всех таблицах, имена которых соответствуют параметру *TableName*и которые принадлежат текущему пользователю. Если текущему пользователю принадлежит таблица, имя которого соответствует *TableName* параметра **SQLColumns** возвращает сведения обо всех таблицах, принадлежащих другим пользователям, в которых соответствует имени таблицы  *TableName* параметра. Для ODBC 2. *x* приложений с использованием подстановочных знаков, **SQLColumns** возвращает все таблицы, имена которых соответствуют параметру *TableName*. Для ODBC 3. *x* приложений **SQLColumns** возвращает все таблицы, имена которых соответствуют параметру *TableName* независимо от владельца или же используются подстановочные знаки.  
  
 В следующей таблице перечислены столбцы, возвращаемые в результирующем наборе.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|DATA_TYPE|Возвращает значение SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для **varchar(max)** типов данных.|  
|TYPE_NAME|Возвращает «varchar», «varbinary» или «nvarchar» для **varchar(max)**, **varbinary(max)**, и **nvarchar(max)** типов данных.|  
|COLUMN_SIZE|Возвращает значение SQL_SS_LENGTH_UNLIMITED для **varchar(max)** данных типа, указывающее, что размер столбца не ограничен.|  
|BUFFER_LENGTH|Возвращает значение SQL_SS_LENGTH_UNLIMITED для **varchar(max)** данных типа, указывающее, что размер буфера не ограничен.|  
|SQL_DATA_TYPE|Возвращает значение SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для **varchar(max)** типов данных.|  
|CHAR_OCTET_LENGTH|Возвращает максимальную длину символьного или двоичного столбца. Возвращает значение 0, если размер не ограничен.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Возвращает имя каталога, в котором определено имя коллекции схем XML. Если обнаружить имя каталога невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Возвращает имя схемы, в которой определено имя коллекции схем XML. Если обнаружить имя схемы невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_NAME|Возвращает имя коллекции схем XML. Если обнаружить имя невозможно, то эта переменная содержит пустую строку.|  
|SS_UDT_CATALOG_NAME|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_UDT_SCHEMA_NAME|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Имя сборки определяемого пользователем типа.|  
  
 Для определяемых пользователем типов столбец TYPE_NAME используется для указания имени определяемого пользователем типа; Поэтому не дополнительный столбец, для него следует добавить результирующий набор **SQLColumns** или [SQLProcedureColumns](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md). DATA_TYPE для столбца или параметра определяемого пользователем типа имеет значение SQL_SS_UDT.  
  
 Для параметров определяемого пользователем типа можно использовать новые, зависящие от драйвера дескрипторы, определенные выше, для получения или задания дополнительных свойств метаданных определяемого пользователем типа, если сервер должен вернуть или запросить данные сведения.  
  
 Когда клиент подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и вызывает SQLColumns, с помощью значения NULL или символы-шаблоны для входного параметра каталога не возвращает сведения из других каталогов. Вместо этого будут возвращены сведения только о текущем каталоге. Во-первых, клиент может вызывать SQLTables, чтобы определить, в каком каталоге находится нужная таблица. Клиент может использовать это значение для входного параметра каталога в его вызов SQLColumns для получения сведений о столбцах этой таблицы.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>Функция SQLColumns и возвращающие табличное значение параметры  
 Результирующий набор, возвращаемый SQLColumns зависит от настройки SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Следующие столбцы добавлены для возвращающих табличное значение параметров.  
  
|Имя столбца|Тип данных|Содержание|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Если столбец является вычисляемым, то для него в TABLE_TYPE это значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, если столбец является столбцом идентификаторов. В противном случае — SQL_FALSE.|  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLColumns улучшенных возможностей работы с датой и временем  
 Сведения о значениях, возвращаемых для типов даты и времени, см. в разделе [метаданные каталога](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLColumns определяемых пользователем типов больших данных CLR  
 **SQLColumns** поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Поддержка функцией SQLColumns разреженных столбцов  
 Два [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определенные столбцы были добавлены к результирующему набору для SQLColumns:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint**|Если столбец является разреженным, то значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_COLUMN_SET|**Smallint**|Если столбец является **column_set** столбца, это значение равно SQL_TRUE; в противном случае — SQL_FALSE.|  
  
 В соответствии со спецификацией ODBC SS_IS_SPARSE и SS_IS_COLUMN_SET появляются перед все специфические для драйвера столбцами, которые были добавлены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]и после всех столбцов, обязательных для ODBC.  
  
 Результирующий набор, возвращаемый SQLColumns зависит от настройки SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Дополнительные сведения о разреженных столбцах в ODBC см. в разделе [Поддержка разреженных столбцов &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLColumns](http://go.microsoft.com/fwlink/?LinkId=59336)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
