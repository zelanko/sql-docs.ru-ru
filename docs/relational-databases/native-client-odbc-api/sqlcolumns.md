---
title: СЗЛКоловы Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: abce98b64da8de6039f81025201cce25269763a6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302613"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **S'LColumns** возвращается SQL_SUCCESS, существуют ли значения для параметров *CatalogName,* *TableName*или *ColumnName.* Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
> [!NOTE]  
>  Для типов больших значений все параметры длины будут возвращены со значением SQL_SS_LENGTH_UNLIMITED.  
  
 **S'LКолонки** могут быть выполнены на статическом курсоре сервера. Попытка выполнить **S'LColumns** на курсоре updatable (динамическом или клавиатурном) вернется SQL_SUCCESS_WITH_INFO, указывающим на изменение типа курсора.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
 Для ODBC 2. *x* приложения, не использующие подстановочные знаки в *TableName,* **S'LColumns,** возвращают информацию о любых таблицах, имена которых соответствуют *TableName* и принадлежат текущему пользователю. Если у текущего пользователя нет таблицы, имя которой совпадает с параметром *TableName,* **S'LColumns** возвращает информацию о любых таблицах, принадлежащих другим пользователям, где имя таблицы совпадает с параметром *TableName.* Для ODBC 2. *x* приложения, использующие подстановочные **знаки, S'LColumns** возвращает все таблицы, имена которых соответствуют *TableName.* Для ODBC 3. *x* приложения **S'LColumns** возвращает все таблицы, имена которых соответствуют *TableName,* независимо от владельца или от использования подстановочных знаков.  
  
 В следующей таблице перечислены столбцы, возвращаемые в результирующем наборе.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|DATA_TYPE|Возвращает SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для типов данных **varchar(max).**|  
|TYPE_NAME|Возвращает "варчар", "варбинарский", или "nvarchar" для **varchar (max)**, **варбинарных (макс)**, и **nvarchar (макс)** типов данных.|  
|COLUMN_SIZE|Возвращает SQL_SS_LENGTH_UNLIMITED для типов данных **varchar(max),** что указывает на то, что размер столбца не ограничен.|  
|BUFFER_LENGTH|Возвращает SQL_SS_LENGTH_UNLIMITED для типов данных **varchar(max),** что указывает на то, что размер буфера не ограничен.|  
|SQL_DATA_TYPE|Возвращает SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR для типов данных **varchar(max).**|  
|CHAR_OCTET_LENGTH|Возвращает максимальную длину символьного или двоичного столбца. Возвращает значение 0, если размер не ограничен.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Возвращает имя каталога, в котором определено имя коллекции схем XML. Если обнаружить имя каталога невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Возвращает имя схемы, в которой определено имя коллекции схем XML. Если обнаружить имя схемы невозможно, то эта переменная содержит пустую строку.|  
|SS_XML_SCHEMACOLLECTION_NAME|Возвращает имя коллекции схем XML. Если обнаружить имя невозможно, то эта переменная содержит пустую строку.|  
|SS_UDT_CATALOG_NAME|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_UDT_SCHEMA_NAME|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Имя сборки определяемого пользователем типа.|  
  
 Для UDT используется существующая TYPE_NAME колонка для обозначения имени UDT; поэтому не следует добавлять дополнительный столбец к набору результатов **S'LColumns** или [S'LProcedureColumns.](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md) DATA_TYPE для столбца или параметра определяемого пользователем типа имеет значение SQL_SS_UDT.  
  
 Для параметров определяемого пользователем типа можно использовать новые, зависящие от драйвера дескрипторы, определенные выше, для получения или задания дополнительных свойств метаданных определяемого пользователем типа, если сервер должен вернуть или запросить данные сведения.  
  
 Когда клиент подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s-LColumns и вызывает вызовы, использование значений NULL или wild card для параметра ввода каталога не возвращает информацию из других каталогов. Вместо этого будут возвращены сведения только о текущем каталоге. Клиент может сначала позвонить в S'LTables, чтобы определить, в каком каталоге находится желаемая таблица. Затем клиент может использовать это значение каталога для параметра ввода каталога в своем вызове к S'LColumns для получения информации о столбцах в этой таблице.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>Функция SQLColumns и возвращающие табличное значение параметры  
 Набор результатов, возвращенный S'LColumns, зависит от настройки SQL_SOPT_SS_NAME_SCOPE. Для получения более подробной информации, [см.](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) Следующие столбцы добавлены для возвращающих табличное значение параметров.  
  
|Имя столбца|Тип данных|Содержимое|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Если столбец является вычисляемым, то для него в TABLE_TYPE это значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, если столбец является столбцом идентификаторов. В противном случае — SQL_FALSE.|  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLColumns улучшенных возможностей работы с датой и временем  
 Для получения информации о значениях, возвращенных для типов дат/времени, [см.](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLColumns определяемых пользователем типов больших данных CLR  
 **S'LColumns** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Поддержка функцией SQLColumns разреженных столбцов  
 К [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набору результатов для S'LColumns добавлены два конкретных столбца:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Смолинт**|Если столбец является разреженным, то значение равно SQL_TRUE. В противном случае — SQL_FALSE.|  
|SS_IS_COLUMN_SET|**Смолинт**|Если столбец является **column_set** столбца, это SQL_TRUE; в противном случае, SQL_FALSE.|  
  
 В соответствии со спецификацией ODBC, SS_IS_SPARSE и SS_IS_COLUMN_SET предстать перед [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всеми [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]драйверами конкретных столбцов, которые были добавлены в версии раньше, чем , и после всех столбцов, предписанных ODBC себя.  
  
 Набор результатов, возвращенный S'LColumns, зависит от настройки SQL_SOPT_SS_NAME_SCOPE. Для получения более подробной информации, [см.](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
 Для получения дополнительной информации о разреженной столбцов в ODBC, см. [Sparse колонки поддержка &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LКолонки](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
