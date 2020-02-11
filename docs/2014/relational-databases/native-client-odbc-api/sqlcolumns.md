---
title: SQLColumns | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5815e4f3a0cdd0defb16c613f3d6e9444fdfaac7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067733"
---
# <a name="sqlcolumns"></a>SQLColumns
  `SQLColumns`Возвращает SQL_SUCCESS, существуют ли значения для параметров *CatalogName*, *TableName*или *ColumnName* . **SQLFetch** возвращает SQL_NO_DATA, если в этих параметрах используются недопустимые значения.  
  
> [!NOTE]  
>  Для типов больших значений все параметры длины будут возвращены со значением SQL_SS_LENGTH_UNLIMITED.  
  
 Метод `SQLColumns` может быть выполнен для статического серверного курсора. При попытке выполнить метод `SQLColumns` для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
 Для ODBC 2. приложения *x* , не использующие подстановочные знаки в `SQLColumns` *TableName*, возвращают сведения обо всех таблицах, имена которых совпадают с *TableName* и принадлежат текущему пользователю. Если текущий пользователь не владеет таблицей, имя которой соответствует ** параметру TableName `SQLColumns` , возвращает сведения о любых таблицах, принадлежащих другим пользователям, где имя таблицы совпадает с параметром *TableName* . Для ODBC 2. приложения *x* , использующие подстановочные `SQLColumns` знаки, возвращает все таблицы, имена которых совпадают с *TableName*. Для ODBC 3. ** приложения `SQLColumns` x возвращают все таблицы, имена которых совпадают с *TableName* , независимо от владельца или от того, используются ли подстановочные знаки.  
  
 В следующей таблице перечислены столбцы, возвращаемые в результирующем наборе.  
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|DATA_TYPE|Возвращает SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для типов данных **varchar (max)** .|  
|TYPE_NAME|Возвращает "varchar", "varbinary" или "nvarchar" для типов данных **varchar (max)**, **varbinary (max)** и **nvarchar (max)** .|  
|COLUMN_SIZE|Возвращает SQL_SS_LENGTH_UNLIMITED для типов данных **varchar (max)** , указывающих на то, что размер столбца не ограничен.|  
|BUFFER_LENGTH|Возвращает SQL_SS_LENGTH_UNLIMITED для типов данных **varchar (max)** , указывающих, что размер буфера не ограничен.|  
|SQL_DATA_TYPE|Возвращает SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для типов данных **varchar (max)** .|  
|CHAR_OCTET_LENGTH|Возвращает максимальную длину символьного или двоичного столбца. Возвращает значение 0, если размер не ограничен.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Возвращает имя каталога, в котором определено имя коллекции схем XML. Если обнаружить имя каталога невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Возвращает имя схемы, в которой определено имя коллекции схем XML. Если обнаружить имя схемы невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_NAME|Возвращает имя коллекции схем XML. Если обнаружить имя невозможно, то эта переменная содержит пустую строку.|  
|SS_UDT_CATALOG_NAME|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_UDT_SCHEMA_NAME|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Имя сборки определяемого пользователем типа.|  
  
 Для определяемых пользователем типов существующий столбец TYPE_NAME используется для указания имени определяемого пользователем типа; Поэтому для него не следует добавлять дополнительный столбец в результирующий набор `SQLColumns` или [SQLProcedureColumns](sqlprocedurecolumns.md). DATA_TYPE для столбца или параметра определяемого пользователем типа имеет значение SQL_SS_UDT.  
  
 Для параметров определяемого пользователем типа можно использовать новые, зависящие от драйвера дескрипторы, определенные выше, для получения или задания дополнительных свойств метаданных определяемого пользователем типа, если сервер должен вернуть или запросить данные сведения.  
  
 Когда клиент подключается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к и вызывает SQLColumns, использование значений NULL или подстановочных знаков для входного параметра каталога не приведет к возврату сведений из других каталогов. Вместо этого будут возвращены сведения только о текущем каталоге. Клиент может сначала вызвать SQLTables, чтобы определить, в каком каталоге находится нужная таблица. Затем клиент может использовать это значение каталога для входного параметра каталога в его вызове SQLColumns для получения сведений о столбцах в этой таблице.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>Функция SQLColumns и возвращающие табличное значение параметры  
 Результирующий набор, возвращаемый функцией SQLColumns, зависит от значения параметра SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md). Следующие столбцы добавлены для возвращающих табличное значение параметров.  
  
|Имя столбца|Тип данных|Содержимое|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Если столбец является вычисляемым, то для него в TABLE_TYPE это значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, если столбец является столбцом идентификаторов. В противном случае — SQL_FALSE.|  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLColumns улучшенных возможностей работы с датой и временем  
 Сведения о значениях, возвращаемых для типов даты и времени, см. в разделе [метаданные каталога](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLColumns определяемых пользователем типов больших данных CLR  
 Функция `SQLColumns` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Поддержка функцией SQLColumns разреженных столбцов  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] результирующий набор для SQLColumns были добавлены два указанных столбца:  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|`Smallint`|Если столбец является разреженным, то значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_COLUMN_SET|`Smallint`|Если столбец является `column_set`, это значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
  
 В соответствии со спецификацией ODBC SS_IS_SPARSE и SS_IS_COLUMN_SET отображаются перед всеми столбцами, которые были добавлены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] более ранние версии, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], и после всех столбцов, заданные самим ODBC.  
  
 Результирующий набор, возвращаемый функцией SQLColumns, зависит от значения параметра SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о разреженных столбцах в ODBC см. в разделе [Поддержка разреженных столбцов &#40;&#41;ODBC ](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLColumns](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
