---
title: "SQLColumns | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 661c678e8d98d1b4d3f88c29d6d0b786b4e686d4
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumns** возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName*, *TableName*, или *ColumnName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
> [!NOTE]  
>  Для типов больших значений все параметры длины будут возвращены со значением SQL_SS_LENGTH_UNLIMITED.  
  
 **SQLColumns** может быть выполнена для статического серверного курсора. Попытка выполнить **SQLColumns** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
 Для ODBC 2. *x* приложения, не использующие подстановочные знаки в *TableName*, **SQLColumns** возвращает сведения обо всех таблицах, имена которых соответствуют *TableName*, принадлежащих текущему пользователю. Если текущему пользователю принадлежит таблица, имя которого соответствует *TableName* параметр **SQLColumns** возвращает сведения обо всех таблицах, принадлежащих другим пользователям, в которых соответствует имени таблицы  *TableName* параметра. Для ODBC 2. *x* приложений с использованием подстановочных знаков, **SQLColumns** возвращает все таблицы, имена которых соответствуют *TableName*. Для ODBC 3. *x* приложений **SQLColumns** возвращает все таблицы, имена которых соответствуют *TableName* независимо от владельца или использования символов-шаблонов.  
  
 В следующей таблице перечислены столбцы, возвращаемые в результирующем наборе.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|DATA_TYPE|Возвращает значение SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для **varchar(max)** типов данных.|  
|TYPE_NAME|Возвращает значение «varchar», «varbinary» или «nvarchar» **varchar(max)**, **varbinary(max)**, и **nvarchar(max)** типов данных.|  
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
  
 Для определяемых пользователем типов столбец TYPE_NAME используется для указания имени определяемого пользователем типа; Поэтому добавить не дополнительный столбец результирующего набора **SQLColumns** или [SQLProcedureColumns](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md). DATA_TYPE для столбца или параметра определяемого пользователем типа имеет значение SQL_SS_UDT.  
  
 Для параметров определяемого пользователем типа можно использовать новые, зависящие от драйвера дескрипторы, определенные выше, для получения или задания дополнительных свойств метаданных определяемого пользователем типа, если сервер должен вернуть или запросить данные сведения.  
  
 Когда клиент подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и вызывает SQLColumns, с помощью значения NULL или символы-шаблоны для входного параметра каталога не возвращает сведения из других каталогов. Вместо этого будут возвращены сведения только о текущем каталоге. Во-первых, клиент может вызывать SQLTables, чтобы определить, в каком каталоге находится нужная таблица. Клиент может использовать это значение входного параметра каталога при вызове SQLColumns для получения сведений о столбцах этой таблицы.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>Функция SQLColumns и возвращающие табличное значение параметры  
 Результирующий набор, возвращенный SQLColumns зависит от настройки SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Следующие столбцы добавлены для возвращающих табличное значение параметров.  
  
|Имя столбца|Тип данных|Содержание|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Если столбец является вычисляемым, то для него в TABLE_TYPE это значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, если столбец является столбцом идентификаторов. В противном случае — SQL_FALSE.|  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLColumns улучшенных возможностей работы с датой и временем  
 Сведения о значениях, возвращаемых для типов даты и времени см. в разделе [метаданные каталога](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLColumns определяемых пользователем типов больших данных CLR  
 **SQLColumns** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Поддержка функцией SQLColumns разреженных столбцов  
 Два [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] были добавлены указанные столбцы в результирующем наборе для SQLColumns:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint**|Если столбец является разреженным, то значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_COLUMN_SET|**Smallint**|Если столбец является **column_set** столбца, это значение равно SQL_TRUE; в противном случае — SQL_FALSE.|  
  
 В соответствии со спецификацией ODBC SS_IS_SPARSE и SS_IS_COLUMN_SET появляются перед все специфические для драйвера столбцами, которые были добавлены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]и после всех столбцов, предоставленных ODBC.  
  
 Результирующий набор, возвращенный SQLColumns зависит от настройки SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Дополнительные сведения о разреженных столбцах в ODBC см. в разделе [Поддержка разреженных столбцов &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLColumns](http://go.microsoft.com/fwlink/?LinkId=59336)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
