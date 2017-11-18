---
title: "Элементы SQLServerDatabaseMetaData | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327ba0bc-438a-494c-b119-1cd4a096bb58
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 47a2c30638f964f04af3b4579cccbb71af1ba65c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverdatabasemetadata-members"></a>Элементы SQLServerDatabaseMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Имя|Description|  
|----------|-----------------|  
|java.sql.DatabaseMetaData|attributeNoNulls, attributeNullable, attributeNullableUnknown, bestRowNotPseudo, bestRowPseudo, bestRowSession, bestRowTemporary, bestRowTransaction, bestRowUnknown, columnNoNulls, columnNullable, columnNullableUnknown, importedKeyCascade, importedKeyInitiallyDeferred, importedKeyInitiallyImmediate, importedKeyNoAction, importedKeyNotDeferrable, importedKeyRestrict, importedKeySetDefault, importedKeySetNull, procedureColumnIn, procedureColumnInOut, procedureColumnOut, procedureColumnResult, procedureColumnReturn, procedureColumnUnknown, procedureNoNulls, procedureNoResult, procedureNullable, procedureNullableUnknown, procedureResultUnknown, procedureReturnsResult, sqlStateSQL, sqlStateSQL99, sqlStateXOpen, tableIndexClustered, tableIndexHashed, tableIndexOther, tableIndexStatistic, typeNoNulls, typeNullable, typeNullableUnknown, typePredBasic, typePredChar, typePredNone, typeSearchable, versionColumnNotPseudo, versionColumnPseudo, versionColumnUnknown|  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[allProceduresAreCallable](../../../connect/jdbc/reference/allproceduresarecallable-method-sqlserverdatabasemetadata.md)|Сообщает, является ли текущий пользователь имеет разрешения на вызов всех процедур, возвращаемых методом [getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md) метод.|  
|[allTablesAreSelectable](../../../connect/jdbc/reference/alltablesareselectable-method-sqlserverdatabasemetadata.md)|Сообщает, является ли текущий пользователь имеет разрешения на использование всех таблиц, возвращаемых функцией [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) метод в инструкции SELECT.|  
|[autoCommitFailureClosesAllResultSets](../../../connect/jdbc/reference/autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata.md)|Указывает, закрывает ли драйвер JDBC все открытые результирующие наборы, включая те, которые допускают удержание, когда при включенном режиме автоматической фиксации возникает исключение.|  
|[dataDefinitionCausesTransactionCommit](../../../connect/jdbc/reference/datadefinitioncausestransactioncommit-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, приводит ли выполнение инструкции определения базы данных в транзакции к фиксации транзакции.|  
|[dataDefinitionIgnoredInTransactions](../../../connect/jdbc/reference/datadefinitionignoredintransactions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли эта база данных инструкции определения данных в пределах транзакции.|  
|[deletesAreDetected](../../../connect/jdbc/reference/deletesaredetected-method-sqlserverdatabasemetadata.md)|Извлекает ли удаление видимой строки могут быть обнаружены путем вызова [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) метод [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса.|  
|[doesMaxRowSizeIncludeBlobs](../../../connect/jdbc/reference/doesmaxrowsizeincludeblobs-method-sqlserverdatabasemetadata.md)|Извлекает ли возвращаемое значение для [getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md) метод включает типы данных SQL LONGVARCHAR и LONGVARBINARY.|  
|[getAttributes](../../../connect/jdbc/reference/getattributes-method-sqlserverdatabasemetadata.md)|Получает описание заданного атрибута заданного типа для определяемого пользователем типа, находящегося в заданной схеме и заданном каталоге.|  
|[getBestRowIdentifier](../../../connect/jdbc/reference/getbestrowidentifier-method-sqlserverdatabasemetadata.md)|Возвращает описание оптимального набора столбцов таблицы, который уникальным образом идентифицирует строку.|  
|[getCatalogs](../../../connect/jdbc/reference/getcatalogs-method-sqlserverdatabasemetadata.md)|Возвращает имена каталогов, доступных на подключенном сервере.|  
|[getCatalogSeparator](../../../connect/jdbc/reference/getcatalogseparator-method-sqlserverdatabasemetadata.md)|Извлекает **строка** , эта база данных используется в качестве разделителя между каталогом и именем таблицы.|  
|[getCatalogTerm](../../../connect/jdbc/reference/getcatalogterm-method-sqlserverdatabasemetadata.md)|Получает эквивалент каталога в терминологии поставщика баз данных.|  
|[getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md)|Извлекает список свойств данных клиентов, поддерживаемых драйвером.|  
|[getColumnPrivileges](../../../connect/jdbc/reference/getcolumnprivileges-method-sqlserverdatabasemetadata.md)|Возвращает описание прав доступа для столбцов в таблице.|  
|[getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md)|Возвращает описание столбцов таблицы, доступных в указанном каталоге.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatabasemetadata.md)|Возвращает соединение, на основе которого был создан этот объект метаданных.|  
|[getCrossReference](../../../connect/jdbc/reference/getcrossreference-method-sqlserverdatabasemetadata.md)|Возвращает описание столбцов внешнего ключа в заданной таблице внешнего ключа, который ссылается на столбцы первичного ключа заданной таблицы первичного ключа.|  
|[getDatabaseMajorVersion](../../../connect/jdbc/reference/getdatabasemajorversion-method-sqlserverdatabasemetadata.md)|Возвращает основной номер версии базы данных.|  
|[getDatabaseMinorVersion](../../../connect/jdbc/reference/getdatabaseminorversion-method-sqlserverdatabasemetadata.md)|Возвращает дополнительный номер версии базы данных.|  
|[getDatabaseProductName](../../../connect/jdbc/reference/getdatabaseproductname-method-sqlserverdatabasemetadata.md)|Возвращает имя данного продукта базы данных.|  
|[getDatabaseProductVersion](../../../connect/jdbc/reference/getdatabaseproductversion-method-sqlserverdatabasemetadata.md)|Возвращает номер версии данного продукта базы данных.|  
|[getDefaultTransactionIsolation](../../../connect/jdbc/reference/getdefaulttransactionisolation-method-sqlserverdatabasemetadata.md)|Получает уровень изоляции транзакций по умолчанию для этой базы данных.|  
|[getDriverMajorVersion](../../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md)|Возвращает основной номер версии данного драйвера JDBC.|  
|[getDriverMinorVersion](../../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md)|Возвращает дополнительный номер версии данного драйвера JDBC.|  
|[getDriverName](../../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md)|Возвращает имя этого драйвера JDBC.|  
|[getDriverVersion](../../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md)|Возвращает номер версии данного драйвера JDBC.|  
|[getExportedKeys](../../../connect/jdbc/reference/getexportedkeys-method-sqlserverdatabasemetadata.md)|Возвращает описание столбцов внешнего ключа, ссылающихся на столбцы первичного ключа заданной таблицы.|  
|[getExtraNameCharacters](../../../connect/jdbc/reference/getextranamecharacters-method-sqlserverdatabasemetadata.md)|Возвращает все дополнительные символы (например, символы a–z, A–Z, 0–9 и _), которые могут использоваться в именах идентификаторов без кавычек.|  
|[getFunctions](../../../connect/jdbc/reference/getfunctions-method-sqlserverdatabasemetadata.md)|Возвращает описание системных и пользовательских функций.|  
|[getFunctionColumns](../../../connect/jdbc/reference/getfunctioncolumns-method-sqlserverdatabasemetadata.md)|Возвращает описание параметров и возвращаемого типа системной или пользовательской функции указанного каталога.|  
|[getIdentifierQuoteString](../../../connect/jdbc/reference/getidentifierquotestring-method-sqlserverdatabasemetadata.md)|Извлекает **строка** , используемый для заключения в кавычки идентификаторов SQL.|  
|[getImportedKeys](../../../connect/jdbc/reference/getimportedkeys-method-sqlserverdatabasemetadata.md)|Возвращает описание столбцов первичного ключа, на которые ссылаются столбцы внешнего ключа таблицы.|  
|[getIndexInfo](../../../connect/jdbc/reference/getindexinfo-method-sqlserverdatabasemetadata.md)|Возвращает описание индексов и статистик заданной таблицы.|  
|[getJDBCMajorVersion](../../../connect/jdbc/reference/getjdbcmajorversion-method-sqlserverdatabasemetadata.md)|Возвращает основной номер версии JDBC для этого драйвера.|  
|[getJDBCMinorVersion](../../../connect/jdbc/reference/getjdbcminorversion-method-sqlserverdatabasemetadata.md)|Возвращает дополнительный номер версии JDBC для этого драйвера.|  
|[getMaxBinaryLiteralLength](../../../connect/jdbc/reference/getmaxbinaryliterallength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, представляющих шестнадцатеричное число, допустимое во встроенных двоичных литералах для этой базы данных.|  
|[getMaxCatalogNameLength](../../../connect/jdbc/reference/getmaxcatalognamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени каталога для этой базы данных.|  
|[getMaxCharLiteralLength](../../../connect/jdbc/reference/getmaxcharliterallength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в символьной константе для этой базы данных.|  
|[getMaxColumnNameLength](../../../connect/jdbc/reference/getmaxcolumnnamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени столбца для этой базы данных.|  
|[getMaxColumnsInGroupBy](../../../connect/jdbc/reference/getmaxcolumnsingroupby-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число столбцов, допустимое в предложении GROUP BY для этой базы данных.|  
|[getMaxColumnsInIndex](../../../connect/jdbc/reference/getmaxcolumnsinindex-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число столбцов, допустимое в индексе для этой базы данных.|  
|[getMaxColumnsInOrderBy](../../../connect/jdbc/reference/getmaxcolumnsinorderby-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число столбцов, допустимое в предложении ORDER BY для этой базы данных.|  
|[getMaxColumnsInSelect](../../../connect/jdbc/reference/getmaxcolumnsinselect-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число столбцов, допустимое в списке SELECT для этой базы данных.|  
|[getMaxColumnsInTable](../../../connect/jdbc/reference/getmaxcolumnsintable-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число столбцов, допустимое в таблице для этой базы данных.|  
|[getMaxConnections](../../../connect/jdbc/reference/getmaxconnections-method-sqlserverdatabasemetadata.md)|Возвращает максимально возможное число одновременных соединений с этой базой данных.|  
|[getMaxCursorNameLength](../../../connect/jdbc/reference/getmaxcursornamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени курсора для этой базы данных.|  
|[getMaxIndexLength](../../../connect/jdbc/reference/getmaxindexlength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число байтов, допустимое в индексе для этой базы данных, включая все части индекса.|  
|[getMaxProcedureNameLength](../../../connect/jdbc/reference/getmaxprocedurenamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени процедуры для этой базы данных.|  
|[getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число байтов, допустимое в одной строке для этой базы данных.|  
|[getMaxSchemaNameLength](../../../connect/jdbc/reference/getmaxschemanamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени схемы для этой базы данных.|  
|[getMaxStatementLength](../../../connect/jdbc/reference/getmaxstatementlength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в инструкции SQL для этой базы данных.|  
|[getMaxStatements](../../../connect/jdbc/reference/getmaxstatements-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число активных инструкций для этой базы данных, которые могут быть открыты одновременно.|  
|[getMaxTableNameLength](../../../connect/jdbc/reference/getmaxtablenamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени таблицы для этой базы данных.|  
|[getMaxTablesInSelect](../../../connect/jdbc/reference/getmaxtablesinselect-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число таблиц, допустимое в инструкции SELECT для этой базы данных.|  
|[getMaxUserNameLength](../../../connect/jdbc/reference/getmaxusernamelength-method-sqlserverdatabasemetadata.md)|Возвращает максимальное число символов, допустимое в имени пользователя для этой базы данных.|  
|[getNumericFunctions](../../../connect/jdbc/reference/getnumericfunctions-method-sqlserverdatabasemetadata.md)|Возвращает список с разделителями-запятыми математических функций, доступных для этой базы данных.|  
|[getPrimaryKeys](../../../connect/jdbc/reference/getprimarykeys-method-sqlserverdatabasemetadata.md)|Возвращает описание столбцов первичного ключа заданной таблицы.|  
|[getProcedureColumns](../../../connect/jdbc/reference/getprocedurecolumns-method-sqlserverdatabasemetadata.md)|Возвращает описание параметров и столбцов результата хранимой процедуры.|  
|[getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md)|Возвращает описание хранимых процедур, доступных в заданном каталоге, схеме или по шаблону имени хранимой процедуры.|  
|[getProcedureTerm](../../../connect/jdbc/reference/getprocedureterm-method-sqlserverdatabasemetadata.md)|Возвращает предпочтительный термин для процедуры в этой базе данных.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverdatabasemetadata.md)|Возвращает возможность удержания результирующих наборов по умолчанию для этой базы данных.|  
|[getRowIdLifetime](../../../connect/jdbc/reference/getrowidlifetime-method-sqlserverdatabasemetadata.md)|Возвращает состояние, указывающее, поддерживается ли тип данных SQL RowId. Если он поддерживается, то возвращает время существования объекта RowId.|  
|[getSchemas](../../../connect/jdbc/reference/getschemas-method.md)|Возвращает имена схем, доступных в текущей базе данных.|  
|[getSchemaTerm](../../../connect/jdbc/reference/getschematerm-method-sqlserverdatabasemetadata.md)|Получает предпочтительный термин для схемы в этой базе данных.|  
|[getSearchStringEscape](../../../connect/jdbc/reference/getsearchstringescape-method-sqlserverdatabasemetadata.md)|Извлекает **строка** , может использоваться для экранирования символов-шаблонов.|  
|[getSQLKeywords](../../../connect/jdbc/reference/getsqlkeywords-method-sqlserverdatabasemetadata.md)|Возвращает список с разделителями-запятыми всех ключевых слов SQL этой базы данных, не входящих в перечень ключевых слов SQL92.|  
|[getSQLStateType](../../../connect/jdbc/reference/getsqlstatetype-method-sqlserverdatabasemetadata.md)|Указывает, равно ли состояние SQLSTATE, возвращенное методом SQLException.getSQLState, X/Open (теперь называется Open Group), SQL CLI, SQL99 (JDBC 3.0) или SQL:2003 (JDBC 4.0).|  
|[getStringFunctions](../../../connect/jdbc/reference/getstringfunctions-method-sqlserverdatabasemetadata.md)|Получает список разделенных запятыми **строка** функции, доступные с этой базой данных.|  
|[getSuperTables](../../../connect/jdbc/reference/getsupertables-method-sqlserverdatabasemetadata.md)|Получает описания иерархий таблиц, определенных в конкретной схеме этой базы данных.|  
|[getSuperTypes](../../../connect/jdbc/reference/getsupertypes-method-sqlserverdatabasemetadata.md)|Получает описание иерархий определяемых пользователем типов, определенных в заданной схеме этой базы данных.|  
|[getSystemFunctions](../../../connect/jdbc/reference/getsystemfunctions-method-sqlserverdatabasemetadata.md)|Возвращает список с разделителями-запятыми системных функций, доступных в этой базе данных.|  
|[getTablePrivileges](../../../connect/jdbc/reference/gettableprivileges-method-sqlserverdatabasemetadata.md)|Возвращает описание прав доступа для каждой таблицы, доступной в заданном каталоге, схеме или по шаблону имени таблицы.|  
|[getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md)|Возвращает описание таблиц, доступных в заданном каталоге, схеме или по шаблону имени таблицы.|  
|[getTableTypes](../../../connect/jdbc/reference/gettabletypes-method-sqlserverdatabasemetadata.md)|Возвращает табличные типы, доступные в текущей базе данных.|  
|[getTimeDateFunctions](../../../connect/jdbc/reference/gettimedatefunctions-method-sqlserverdatabasemetadata.md)|Возвращает список с разделителями-запятыми функций даты и времени, доступных для этой базы данных.|  
|[getTypeInfo](../../../connect/jdbc/reference/gettypeinfo-method-sqlserverdatabasemetadata.md)|Извлекает описание всех стандартных типов SQL, которые поддерживаются в текущей базе данных.|  
|[getUDTs](../../../connect/jdbc/reference/getudts-method-sqlserverdatabasemetadata.md)|Возвращает описание определяемых пользователем типов, определенных в конкретной схеме.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatabasemetadata.md)|Возвращает URL-адрес для этой базы данных.|  
|[getUserName](../../../connect/jdbc/reference/getusername-method-sqlserverdatabasemetadata.md)|Возвращает имя пользователя, как оно известно в базе данных.|  
|[getVersionColumns](../../../connect/jdbc/reference/getversioncolumns-method-sqlserverdatabasemetadata.md)|Возвращает описание столбцов таблицы, которые автоматически обновляются при обновлении любого значения в строке.|  
|[insertsAreDetected](../../../connect/jdbc/reference/insertsaredetected-method-sqlserverdatabasemetadata.md)|Извлекает ли вставка видимой строки могут быть обнаружены путем вызова метода [rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md) метод [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса.|  
|[isCatalogAtStart](../../../connect/jdbc/reference/iscatalogatstart-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, находится ли каталог в начале полного имени таблицы.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, находится ли эта база данных в режиме только для чтения.|  
|[locatorsUpdateCopy](../../../connect/jdbc/reference/locatorsupdatecopy-method-sqlserverdatabasemetadata.md)|Указывает, будут ли обновления в LOB производиться над этим объектом LOB напрямую, либо над его копией.|  
|[nullPlusNonNullIsNull](../../../connect/jdbc/reference/nullplusnonnullisnull-method-sqlserverdatabasemetadata.md)|Указывает, поддерживает ли эта база данных получение значений NULL в результате объединения значений NULL и значений, отличных от NULL.|  
|[nullsAreSortedAtEnd](../../../connect/jdbc/reference/nullsaresortedatend-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, размещаются ли значения NULL в конце независимо от порядка сортировки.|  
|[nullsAreSortedAtStart](../../../connect/jdbc/reference/nullsaresortedatstart-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, размещаются ли значения NULL в начале независимо от порядка сортировки.|  
|[nullsAreSortedHigh](../../../connect/jdbc/reference/nullsaresortedhigh-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, считаются ли значения NULL большими при сортировке.|  
|[nullsAreSortedLow](../../../connect/jdbc/reference/nullsaresortedlow-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, считаются ли значения NULL маленькими при сортировке.|  
|[othersDeletesAreVisible](../../../connect/jdbc/reference/othersdeletesarevisible-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, являются ли видимыми операции удаления, выполненные другими пользователями.|  
|[othersInsertsAreVisible](../../../connect/jdbc/reference/othersinsertsarevisible-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, являются ли видимыми операции вставки, выполненные другими пользователями.|  
|[othersUpdatesAreVisible](../../../connect/jdbc/reference/othersupdatesarevisible-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, являются ли видимыми операции обновления, выполненные другими пользователями.|  
|[ownDeletesAreVisible](../../../connect/jdbc/reference/owndeletesarevisible-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, являются ли видимыми собственные операции удаления результирующего набора.|  
|[ownInsertsAreVisible](../../../connect/jdbc/reference/owninsertsarevisible-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, являются ли видимыми собственные операции вставки результирующего набора.|  
|[ownUpdatesAreVisible](../../../connect/jdbc/reference/ownupdatesarevisible-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, являются ли видимыми собственные операции обновления результирующего набора.|  
|[storesLowerCaseIdentifiers](../../../connect/jdbc/reference/storeslowercaseidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет ли их в нижнем регистре.|  
|[storesLowerCaseQuotedIdentifiers](../../../connect/jdbc/reference/storeslowercasequotedidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, заключенных в кавычки, и сохраняет их в нижнем регистре.|  
|[storesMixedCaseIdentifiers](../../../connect/jdbc/reference/storesmixedcaseidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет их в смешанном регистре.|  
|[storesMixedCaseQuotedIdentifiers](../../../connect/jdbc/reference/storesmixedcasequotedidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, заключенных в кавычки, и сохраняет их в смешанном регистре.|  
|[storesUpperCaseIdentifiers](../../../connect/jdbc/reference/storesuppercaseidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет их в верхнем регистре.|  
|[storesUpperCaseQuotedIdentifiers](../../../connect/jdbc/reference/storesuppercasequotedidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, заключенных в кавычки, и сохраняет их в верхнем регистре.|  
|[supportsAlterTableWithAddColumn](../../../connect/jdbc/reference/supportsaltertablewithaddcolumn-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных инструкцию ALTER TABLE с добавлением столбца.|  
|[supportsAlterTableWithDropColumn](../../../connect/jdbc/reference/supportsaltertablewithdropcolumn-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных инструкцию ALTER TABLE с удалением столбца.|  
|[supportsANSI92EntryLevelSQL](../../../connect/jdbc/reference/supportsansi92entrylevelsql-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных грамматику SQL начального уровня ANSI92.|  
|[supportsANSI92FullSQL](../../../connect/jdbc/reference/supportsansi92fullsql-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных полную грамматику SQL ANSI92.|  
|[supportsANSI92IntermediateSQL](../../../connect/jdbc/reference/supportsansi92intermediatesql-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных промежуточную грамматику SQL начального уровня ANSI92.|  
|[supportsBatchUpdates](../../../connect/jdbc/reference/supportsbatchupdates-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных пакетное обновление.|  
|[supportsCatalogsInDataManipulation](../../../connect/jdbc/reference/supportscatalogsindatamanipulation-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя каталога использоваться в инструкции обработки данных.|  
|[supportsCatalogsInIndexDefinitions](../../../connect/jdbc/reference/supportscatalogsinindexdefinitions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя каталога использоваться в инструкции определения индекса.|  
|[supportsCatalogsInPrivilegeDefinitions](../../../connect/jdbc/reference/supportscatalogsinprivilegedefinitions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя каталога использоваться в инструкции определения права доступа.|  
|[supportsCatalogsInProcedureCalls](../../../connect/jdbc/reference/supportscatalogsinprocedurecalls-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя каталога использоваться в инструкциях вызова процедуры.|  
|[supportsCatalogsInTableDefinitions](../../../connect/jdbc/reference/supportscatalogsintabledefinitions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя каталога использоваться в инструкции определения таблицы.|  
|[supportsColumnAliasing](../../../connect/jdbc/reference/supportscolumnaliasing-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных псевдонимы столбцов.|  
|[supportsConvert](../../../connect/jdbc/reference/supportsconvert-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных функцию CONVERT для преобразования типов SQL.|  
|[supportsCoreSQLGrammar](../../../connect/jdbc/reference/supportscoresqlgrammar-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных базовую SQL-грамматику ODBC.|  
|[supportsCorrelatedSubqueries](../../../connect/jdbc/reference/supportscorrelatedsubqueries-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных связанные вложенные запросы.|  
|[supportsDataDefinitionAndDataManipulationTransactions](../../../connect/jdbc/reference/supportsdatadefinitionanddatamanipulationtransactions-method.md)|Возвращает значение, определяющее, поддерживает ли эта база данных и инструкции определения, и инструкции обработки данных в транзакции.|  
|[supportsDataManipulationTransactionsOnly](../../../connect/jdbc/reference/supportsdatamanipulationtransactionsonly-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных только инструкции обработки данных в транзакции.|  
|[supportsDifferentTableCorrelationNames](../../../connect/jdbc/reference/supportsdifferenttablecorrelationnames-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, что, когда поддерживаются корреляционные имена таблиц, они должны отличаться от имен таблиц.|  
|[supportsExpressionsInOrderBy](../../../connect/jdbc/reference/supportsexpressionsinorderby-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных выражения в списках ORDER BY.|  
|[supportsExtendedSQLGrammar](../../../connect/jdbc/reference/supportsextendedsqlgrammar-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных расширенную SQL-грамматику ODBC.|  
|[supportsFullOuterJoins](../../../connect/jdbc/reference/supportsfullouterjoins-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных полные вложенные внешние соединения.|  
|[supportsGetGeneratedKeys](../../../connect/jdbc/reference/supportsgetgeneratedkeys-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, возможно ли получение автоматически сформированных ключей после выполнения инструкции.|  
|[supportsGroupBy](../../../connect/jdbc/reference/supportsgroupby-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных определенный формат предложения GROUP BY.|  
|[supportsGroupByBeyondSelect](../../../connect/jdbc/reference/supportsgroupbybeyondselect-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных использование в предложении GROUP BY столбцов, отсутствующих в инструкции SELECT, при условии, что все столбцы в инструкции SELECT включены в предложение GROUP BY.|  
|[supportsGroupByUnrelated](../../../connect/jdbc/reference/supportsgroupbyunrelated-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных использование в предложении GROUP BY столбцов, отсутствующих в инструкции SELECT.|  
|[supportsIntegrityEnhancementFacility](../../../connect/jdbc/reference/supportsintegrityenhancementfacility-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных расширенный контроль целостности SQL.|  
|[supportsLikeEscapeClause](../../../connect/jdbc/reference/supportslikeescapeclause-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных экранирование в предложении LIKE.|  
|[supportsLimitedOuterJoins](../../../connect/jdbc/reference/supportslimitedouterjoins-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, обеспечивает ли эта база данных ограниченную поддержку для внешних соединений.|  
|[supportsMinimumSQLGrammar](../../../connect/jdbc/reference/supportsminimumsqlgrammar-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных минимальную SQL-грамматику ODBC.|  
|[supportsMixedCaseIdentifiers](../../../connect/jdbc/reference/supportsmixedcaseidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет их в смешанном регистре.|  
|[supportsMixedCaseQuotedIdentifiers](../../../connect/jdbc/reference/supportsmixedcasequotedidentifiers-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, заключенных в кавычки, и сохраняет их в смешанном регистре.|  
|[supportsMultipleOpenResults](../../../connect/jdbc/reference/supportsmultipleopenresults-method-sqlserverdatabasemetadata.md)|Сообщает, является ли можно иметь несколько [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектами, возвращаемыми [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) объекта одновременно.|  
|[supportsMultipleResultSets](../../../connect/jdbc/reference/supportsmultipleresultsets-method-sqlserverdatabasemetadata.md)|Сообщает, является ли эта база данных поддерживает несколько [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов из одного вызова [выполнение](../../../connect/jdbc/reference/execute-method.md) метод [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)класса.|  
|[supportsMultipleTransactions](../../../connect/jdbc/reference/supportsmultipletransactions-method-sqlserverdatabasemetadata.md)|Извлекает значение, указывающее, поддерживается ли в этой базе данных одновременное открытие нескольких транзакций в различных соединениях.|  
|[supportsNamedParameters](../../../connect/jdbc/reference/supportsnamedparameters-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных именованные параметры в вызываемых инструкциях.|  
|[supportsNonNullableColumns](../../../connect/jdbc/reference/supportsnonnullablecolumns-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, могут ли столбцы в этой базе данных быть определены как не допускающие значения NULL.|  
|[supportsOpenCursorsAcrossCommit](../../../connect/jdbc/reference/supportsopencursorsacrosscommit-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных сохранение курсоров открытыми между фиксациями транзакций.|  
|[supportsOpenCursorsAcrossRollback](../../../connect/jdbc/reference/supportsopencursorsacrossrollback-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных сохранение курсоров открытыми между откатами транзакций.|  
|[supportsOpenStatementsAcrossCommit](../../../connect/jdbc/reference/supportsopenstatementsacrosscommit-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных сохранение инструкций открытыми между фиксациями транзакций.|  
|[supportsOpenStatementsAcrossRollback](../../../connect/jdbc/reference/supportsopenstatementsacrossrollback-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных сохранение инструкций открытыми между откатами транзакций.|  
|[supportsOrderByUnrelated](../../../connect/jdbc/reference/supportsorderbyunrelated-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных использование в предложении ORDER BY столбцов, отсутствующих в инструкции SELECT.|  
|[supportsOuterJoins](../../../connect/jdbc/reference/supportsouterjoins-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных заданный формат внешних соединений.|  
|[supportsPositionedDelete](../../../connect/jdbc/reference/supportspositioneddelete-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных позиционированные инструкции DELETE.|  
|[supportsPositionedUpdate](../../../connect/jdbc/reference/supportspositionedupdate-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных позиционированные инструкции UPDATE.|  
|[supportsResultSetConcurrency](../../../connect/jdbc/reference/supportsresultsetconcurrency-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных заданный тип параллелизма в сочетании с заданным типом результирующего набора.|  
|[supportsResultSetHoldability](../../../connect/jdbc/reference/supportsresultsetholdability-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных заданную возможность сохранения результирующих наборов.|  
|[supportsResultSetType](../../../connect/jdbc/reference/supportsresultsettype-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных заданный тип результирующих наборов.|  
|[supportsSavepoints](../../../connect/jdbc/reference/supportssavepoints-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных точки сохранения.|  
|[supportsSchemasInDataManipulation](../../../connect/jdbc/reference/supportsschemasindatamanipulation-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя схемы использоваться в инструкциях обработки данных.|  
|[supportsSchemasInIndexDefinitions](../../../connect/jdbc/reference/supportsschemasinindexdefinitions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя схемы использоваться в инструкции определения индекса.|  
|[supportsSchemasInPrivilegeDefinitions](../../../connect/jdbc/reference/supportsschemasinprivilegedefinitions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя схемы использоваться в инструкции определения права доступа.|  
|[supportsSchemasInProcedureCalls](../../../connect/jdbc/reference/supportsschemasinprocedurecalls-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя схемы использоваться в инструкциях вызова процедуры.|  
|[supportsSchemasInTableDefinitions](../../../connect/jdbc/reference/supportsschemasintabledefinitions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, может ли имя схемы использоваться в инструкции определения таблицы.|  
|[supportsSelectForUpdate](../../../connect/jdbc/reference/supportsselectforupdate-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных инструкции SELECT FOR UPDATE.|  
|[supportsStatementPooling](../../../connect/jdbc/reference/supportsstatementpooling-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных пулы инструкций.|  
|[supportsStoredFunctionsUsingCallSyntax](../../../connect/jdbc/reference/supportsstoredfunctionsusingcallsyntax-method-sqlserverdatabasemetadata.md)|Указывает, поддерживает ли текущая база данных вызов определяемых пользователем или поставщиком функций с использованием синтаксиса escape-последовательностей в хранимых процедурах.|  
|[supportsStoredProcedures](../../../connect/jdbc/reference/supportsstoredprocedures-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных вызовы хранимых процедур с использованием синтаксиса перехода.|  
|[supportsSubqueriesInComparisons](../../../connect/jdbc/reference/supportssubqueriesincomparisons-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в выражениях сравнения.|  
|[supportsSubqueriesInExists](../../../connect/jdbc/reference/supportssubqueriesinexists-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в выражениях EXISTS.|  
|[supportsSubqueriesInIns](../../../connect/jdbc/reference/supportssubqueriesinins-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в инструкциях IN.|  
|[supportsSubqueriesInQuantifieds](../../../connect/jdbc/reference/supportssubqueriesinquantifieds-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в выражениях с квантором.|  
|[supportsTableCorrelationNames](../../../connect/jdbc/reference/supportstablecorrelationnames-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных корреляционные имена таблиц.|  
|[supportsTransactionIsolationLevel](../../../connect/jdbc/reference/supportstransactionisolationlevel-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных заданный уровень изоляции транзакции.|  
|[supportsTransactions](../../../connect/jdbc/reference/supportstransactions-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных транзакции.|  
|[supportsUnion](../../../connect/jdbc/reference/supportsunion-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных SQL UNION.|  
|[supportsUnionAll](../../../connect/jdbc/reference/supportsunionall-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, поддерживает ли эта база данных SQL UNION ALL.|  
|[updatesAreDetected](../../../connect/jdbc/reference/updatesaredetected-method-sqlserverdatabasemetadata.md)|Извлекает ли обновление видимой строки могут быть обнаружены путем вызова [rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md) метод [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса.|  
|[usesLocalFilePerTable](../../../connect/jdbc/reference/useslocalfilepertable-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, хранит ли база данных каждую таблицу в отдельном файле.|  
|[usesLocalFiles](../../../connect/jdbc/reference/useslocalfiles-method-sqlserverdatabasemetadata.md)|Возвращает значение, определяющее, хранит ли база данных таблицы в локальном файле.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

