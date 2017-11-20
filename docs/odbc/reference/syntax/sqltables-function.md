---
title: "Функция SQLTables | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLTables
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTables
helpviewer_keywords:
- SQLTables function [ODBC]
ms.assetid: 60d5068a-7d7c-447c-acc6-f3f2cf73440c
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd6e505ee08d7162ef820c7c7c75195b3616e585
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqltables-function"></a>Функция SQLTables
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: Open Group  
  
 **Сводка**  
 **SQLTables** возвращает список имен таблиц, каталога или схемы и табличные типы, хранимые в источнике данных. Драйвер возвращает данные в виде результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLTables(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      TableType,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции для получения результатов.  
  
 *CatalogName*  
 [Вход] Имя каталога. *CatalogName* аргумент принимает шаблонов поиска, если атрибут среды SQL_ODBC_VERSION SQL_OV_ODBC3; он не поддерживает шаблоны поиска, если SQL_OV_ODBC2 имеет значение. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») указывает те таблицы, которые не имеют каталоги.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *CatalogName* имеет значение аргумента шаблона; он интерпретируется буквально и его регистр имеет значения. Дополнительные сведения см. в разделе [аргументов функций каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Вход] Длина в символах **CatalogName*.  
  
 *SchemaName*  
 [Вход] Строка, шаблон поиска для имен схемы. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») указывает те таблицы, которые не имеют схемы.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *SchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *SchemaName* имеет значение аргумента шаблона; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength2*  
 [Вход] Длина в символах **SchemaName*.  
  
 *Имя_таблицы*  
 [Вход] Строка шаблона поиска для имен таблиц.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *TableName* имеет значение аргумента шаблона; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength3*  
 [Вход] Длина в символах **TableName*.  
  
 *TableType*  
 [Вход] Список типов таблицы для сопоставления.  
  
 Обратите внимание, что атрибут инструкции SQL_ATTR_METADATA_ID не влияют на *TableType* аргумент. *TableType* значение списка аргумент, независимо от параметра SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 [Вход] Длина в символах **TableType*.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLTables** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLTables** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|Курсор был открыт на *StatementHandle*, и **SQLFetch** или **SQLFetchScroll** бы была вызвана. Если эта ошибка возвращается диспетчером драйверов **SQLFetch** или **SQLFetchScroll** не вернула значение SQL_NO_DATA и возвращается с помощью драйвера, если **SQLFetch** или **SQLFetchScroll** вернула значение SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle*, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|Атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE, *CatalogName* аргумент был пустым указателем, а SQL_CATALOG_NAME *свойство* возвращает которых имена каталога поддерживаются.<br /><br /> (DM) атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE и *SchemaName* или *TableName* аргумент был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. При вызове SQLTables по-прежнему выполнении асинхронной функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длины был меньше 0, но не равно SQL_NTS.<br /><br /> Значение одного из аргументов длина имени превышает значение максимальной длины для соответствующего имени.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Был указан каталог, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Схема была указана и драйвера или источник данных не поддерживает схемы.<br /><br /> Шаблон поиска строки было указано имя каталога, схемы таблицы или имя таблицы и источник данных не поддерживает шаблоны поиска для одного или нескольких из этих аргументов.<br /><br /> Сочетание текущих настроек атрибуты инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_VARIABLE, а атрибут инструкции SQL_ATTR_CURSOR_TYPE был задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Прежде чем источника данных, запрошенный результирующий набор истечения времени ожидания запроса. Время ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 **SQLTables** перечисляются все таблицы в запрошенный диапазон. Пользователь может или не может обладать ОСОБЫМИ правами на любой из этих таблиц. Чтобы проверить доступность, то приложение может:  
  
-   Вызовите **SQLGetInfo** и проверьте тип данных SQL_ACCESSIBLE_TABLES.  
  
-   Вызовите **SQLTablePrivileges** для проверки права доступа для каждой таблицы.  
  
 В противном случае приложения должен уметь обрабатывать ситуацию, где пользователь выбирает таблицу, для которой **ВЫБЕРИТЕ** не предоставлены права.  
  
 *SchemaName* и *TableName* аргументы поддерживает шаблоны из поиска. *CatalogName* аргумент принимает шаблонов поиска, если атрибут среды SQL_ODBC_VERSION SQL_OV_ODBC3; он не поддерживает шаблоны поиска, если SQL_OV_ODBC2 имеет значение. Если задано значение SQL_OV_ODBC3, ODBC 3*.x* требуется драйвер, подстановочные знаки в *CatalogName* экранировать аргумент интерпретируется буквально. Дополнительные сведения о шаблонах допустимые поиска см. в разделе [значения аргументов шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Следующие особой семантики для поддержки перечисления каталогов, схем и табличные типы, определенные для *CatalogName*, *SchemaName*, *TableName*и  *TableType* аргументы **SQLTables**:  
  
-   Если *CatalogName* имеет значение SQL_ALL_CATALOGS и *SchemaName* и *TableName* являются пустыми строками, результирующий набор содержит список каталогов, допустимый для источника данных. (Все столбцы, кроме TABLE_CAT столбца содержать значения NULL).  
  
-   Если *SchemaName* — SQL_ALL_SCHEMAS и *CatalogName* и *TableName* являются пустыми строками, результирующий набор содержит список допустимых схем для источника данных. (Все столбцы, кроме по значениям TABLE_SCHEM столбца содержать значения NULL).  
  
-   Если *TableType* — SQL_ALL_TABLE_TYPES и *CatalogName*, *SchemaName*, и *TableName* являются пустыми строками, результирующий набор содержит список типов допустимую таблицу для источника данных. (Все столбцы, кроме TABLE_TYPE столбца содержать значения NULL).  
  
 Если *TableType* не является пустой строкой, он должен содержать список разделенных запятыми значений для типов, представляющие интерес; каждого значения могут быть заключены в одинарные кавычки (') или не заключаться в кавычки, например «И ТАБЛИЦЕЙ», «Просмотр» или таблицы, ПРЕДСТАВЛЕНИЯ. Приложения всегда следует указывать тип таблицы в верхнем регистре; драйвер следует преобразовать различает необходим источник данных в виде таблицы. Если источник данных не поддерживает тип указанного таблицы **SQLTables** не возвращает никаких результатов для этого типа.  
  
 **SQLTables** возвращает результаты в виде стандартных результирующий набор, упорядоченный по TABLE_TYPE, TABLE_CAT, по значениям TABLE_SCHEM и TABLE_NAME. Сведения о том, как эти сведения может использоваться в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Чтобы определить фактический длин столбцов TABLE_CAT, по значениям TABLE_SCHEM и имя_таблицы, приложение может вызвать **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN и SQL_MAX_TABLE_NAME_LEN сведения типы.  
  
 Следующие столбцы были переименованы для ODBC 3*.x*. Имя столбца изменения не влияют на обратной совместимости так, как привязать приложений, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3*.x* столбца|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Драйвер можно определить дополнительные столбцы вслед за столбец 5 (примечания). Приложения должны доступа специфические для драйвера столбцами путем отсчет от конца результирующего набора вместо указания явного порядковый номер. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Имя каталога; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет каталоги.|  
|ПО ЗНАЧЕНИЯМ TABLE_SCHEM (ODBC 1.0)|2|Varchar|Имя схемы; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|ИМЯ_ТАБЛИЦЫ (ODBC 1.0)|3|Varchar|Имя таблицы.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Имя табличного типа; одно из следующих: «TABLE», «ПРЕДСТАВЛЕНИЕ», «СИСТЕМНАЯ таблица», «ГЛОБАЛЬНЫХ ВРЕМЕННЫХ», «ЛОКАЛЬНЫЕ ВРЕМЕННЫЕ», «ALIAS», «СИНОНИМ» или имя типа, определяемые источником данных.<br /><br /> Значения «ALIAS» и «СИНОНИМ» зависят от конкретного драйвера.|  
|ПРИМЕЧАНИЯ (ODBC 1.0)|5|Varchar|Описание таблицы.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода не позволяет освободить дескрипторы и подключения. В разделе [SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md) и [SQLFreeStmt, функция](../../../odbc/reference/syntax/sqlfreestmt-function.md) образцы кода для освобождения дескрипторов и инструкций.  
  
```  
// SQLTables.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
// simple helper functions  
int MySQLSuccess(SQLRETURN rc) {  
   return (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO);  
}  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printCatalog(const struct DataBinding* catalogResult) {  
   if (catalogResult[0].StrLen_or_Ind != SQL_NULL_DATA)   
      printf("Catalog Name = %s\n", (char *)catalogResult[0].TargetValuePtr);  
}  
  
// remember to disconnect and free memory, and free statements and handles  
int main() {  
   int bufferSize = 1024, i, numCols = 5;  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   wchar_t* dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   wchar_t* userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR*)"Driver={SQL Server}", SQL_NTS, (SQLCHAR*)connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
  
   bufferSize = 1024;  
  
   // allocate memory for the binding  
   // free this memory when done  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // setup the binding (can be used even if the statement is closed by closeStatementHandle)  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   // all catalogs query  
   printf( "A list of names of all catalogs\n" );  
   retCode = SQLTables( hstmt, (SQLCHAR*)SQL_ALL_CATALOGS, SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS );  
   for ( retCode = SQLFetch(hstmt) ;  MySQLSuccess(retCode) ; retCode = SQLFetch(hstmt) )  
      printCatalog( catalogResult );  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение права доступа для столбца или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Возврат столбцов в таблице или таблицах|[Функция SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение статистики таблиц и индексов|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возвращение права доступа для таблицы или таблиц|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)

