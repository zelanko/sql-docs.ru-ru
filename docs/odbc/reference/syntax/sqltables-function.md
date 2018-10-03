---
title: Функция SQLTables | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0930f61ea43fb77e93b9b3ebcb9d20073f1950d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708362"
---
# <a name="sqltables-function"></a>Функция SQLTables
**Соответствие стандартам**  
 Версия была введена: ODBC 1.0 соответствует стандартам: Open Group  
  
 **Сводка**  
 **SQLTables** возвращает список имен таблиц, каталога или схемы и табличные типы, хранящиеся в источнике данных. Драйвер возвращает данные в виде результирующего набора.  
  
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
 [Вход] Имя каталога. *CatalogName* аргумент принимает шаблонов поиска, если атрибут среды SQL_ODBC_VERSION значение SQL_OV_ODBC3; он не поддерживает шаблоны поиска, если SQL_OV_ODBC2 имеет значение. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("») указывает, эти таблицы, у которых нет каталогов.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *CatalogName* — это аргумент значения шаблона; интерпретируется буквально, а также его регистр имеет значения. Дополнительные сведения см. в разделе [аргументов в функции работы с каталогами](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Вход] Длина в символах **CatalogName*.  
  
 *SchemaName*  
 [Вход] Строка шаблона поиска для имен схемы. Если драйвер поддерживает схемы, для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("») указывает, эти таблицы, у которых нет схемы.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *SchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *SchemaName* — это аргумент значения шаблона; интерпретируется буквально, а также его регистр имеет значения.  
  
 *NameLength2*  
 [Вход] Длина в символах **SchemaName*.  
  
 *TableName*  
 [Вход] Строка, шаблон поиска для имен таблиц.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *TableName* — это аргумент значения шаблона; интерпретируется буквально, а также его регистр имеет значения.  
  
 *NameLength3*  
 [Вход] Длина в символах **TableName*.  
  
 *TableType*  
 [Вход] Список типов таблицы для сопоставления.  
  
 Обратите внимание на то, что атрибут инструкции SQL_ATTR_METADATA_ID не влияет на *TableType* аргумент. *TableType* — это значение списка аргумент, независимо от значения SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 [Вход] Длина в символах **TableType*.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLTables** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLTables** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|Курсор был открыт на *StatementHandle*, и **SQLFetch** или **SQLFetchScroll** бы вызывалась. Если эта ошибка возвращается диспетчером драйверов **SQLFetch** или **SQLFetchScroll** не вернула значение SQL_NO_DATA и возвращается с помощью драйвера, если **SQLFetch** или **SQLFetchScroll** вернула значение SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle*, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Выполнен откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Состояние транзакции неизвестно|Не удалось выполнить связанное соединение во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимая для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция был снова вызван для *StatementHandle*.<br /><br /> Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|Атрибут инструкции SQL_ATTR_METADATA_ID было установлено значение SQL_TRUE, *CatalogName* аргумент был пустым указателем, а также SQL_CATALOG_NAME *InfoType* возвращает этот каталога имена поддерживаются.<br /><br /> (DM) атрибут инструкции SQL_ATTR_METADATA_ID было установлено значение SQL_TRUE и *SchemaName* или *TableName* аргумент был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. При вызове функции SQLTables по-прежнему выполнении асинхронной функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длина меньше 0, но не равно SQL_NTS.<br /><br /> Значение одного из аргументов длина имени превышает значение максимальной длины для соответствующего имени.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Был указан каталог, а драйверу или источнику данных не поддерживает каталоги.<br /><br /> Указано схему и драйверу или источнику данных не поддерживает схемы.<br /><br /> Шаблон поиска строки было указано имя каталога, схемы таблицы или имя таблицы и источник данных не поддерживает шаблоны поиска для одного или нескольких из этих аргументов.<br /><br /> Сочетание текущие значения атрибутов инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было присвоено SQL_UB_VARIABLE и атрибут инструкции SQL_ATTR_CURSOR_TYPE было присвоено тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Истекло время ожидания запроса перед источника данных, возвращаемого набора требуемого результата. Период ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 **SQLTables** выводит список всех таблиц в запрошенном диапазоне. Пользователь может иметь или не иметь правами доступа SELECT к любому из этих таблиц. Чтобы проверить доступность, то приложение может:  
  
-   Вызовите **SQLGetInfo** и проверьте тип SQL_ACCESSIBLE_TABLES сведения.  
  
-   Вызовите **SQLTablePrivileges** проверяемый привилегии для каждой таблицы.  
  
 В противном случае приложение должно быть возможность обрабатывать ситуацию, где пользователь выбирает таблицу, для которого **ВЫБЕРИТЕ** права не предоставляются.  
  
 *SchemaName* и *TableName* аргументы принимают шаблонов поиска. *CatalogName* аргумент принимает шаблонов поиска, если атрибут среды SQL_ODBC_VERSION значение SQL_OV_ODBC3; он не поддерживает шаблоны поиска, если SQL_OV_ODBC2 имеет значение. Если задано значение SQL_OV_ODBC3, ODBC 3 *.x* требуется драйвер, подстановочные знаки в *CatalogName* экранировать аргумент интерпретируется буквально. Дополнительные сведения о шаблонах допустимым поиска см. в разделе [аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC, см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Для поддержки перечисления каталогов, схем и табличные типы, определенные следующие особой семантики для *CatalogName*, *SchemaName*, *TableName*и  *TableType* аргументы **SQLTables**:  
  
-   Если *CatalogName* имеет значение SQL_ALL_CATALOGS и *SchemaName* и *TableName* представляют собой пустые строки, результирующий набор содержит список каталогов, допустимый для источника данных. (Все столбцы, кроме TABLE_CAT столбец содержать значения NULL).  
  
-   Если *SchemaName* — SQL_ALL_SCHEMAS и *CatalogName* и *TableName* представляют собой пустые строки, результирующий набор содержит список допустимые схемы для источника данных. (Все столбцы, кроме по значениям TABLE_SCHEM столбец содержать значения NULL).  
  
-   Если *TableType* — SQL_ALL_TABLE_TYPES и *CatalogName*, *SchemaName*, и *TableName* представляют собой пустые строки результирующего набора содержит список типов допустимую таблицу для источника данных. (Все столбцы, кроме TABLE_TYPE столбец содержать значения NULL).  
  
 Если *TableType* не является пустой строкой, он должен содержать список значений с разделителями запятыми для типов интерес; каждого значения могут быть заключены в одинарные кавычки (') или не заключаться в кавычки, например, «TABLE», «Просмотр» или таблицы, просмотр. Приложение всегда следует указывать тип таблицы в верхнем регистре; драйвер следует преобразовать тип таблицы различает регистр необходим источник данных. Если источник данных не поддерживает тип указанной таблицы, **SQLTables** не возвращает никаких результатов для этого типа.  
  
 **SQLTables** возвращает результаты в виде стандартных результирующий набор, упорядоченный по TABLE_TYPE, TABLE_CAT, по значениям TABLE_SCHEM и TABLE_NAME. Сведения о том, как эта информация может использоваться, см. в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Чтобы определить фактический длин столбцов TABLE_CAT, по значениям TABLE_SCHEM и TABLE_NAME, приложение может вызвать **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN и SQL_MAX_TABLE_NAME_LEN сведения типы.  
  
 Следующие столбцы были переименованы для ODBC 3 *.x*. Изменения имен столбцов не влияют на обратную совместимость так, как выполнить привязку приложения, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3 *.x* столбца|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Дополнительные столбцы вслед за столбец 5 ("Примечания") можно определить с помощью драйвера. Приложение должно получить доступ к от драйвера, отсчет от конца результирующего набора вместо указания явной порядковый. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Имя каталога; Значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, возвращается пустая строка ("») для этих таблиц, у которых нет каталогов.|  
|ПО ЗНАЧЕНИЯМ TABLE_SCHEM (ODBC 1.0)|2|Varchar|Имя схемы; Значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|Имя таблицы.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Имя типа таблицы; одно из следующих: «Таблица», «ПРЕДСТАВЛЕНИЕ», «СИСТЕМНАЯ таблица», «Глобальный ВРЕМЕННЫЙ», «ЛОКАЛЬНЫЙ ВРЕМЕННЫЙ», «ALIAS», «СИНОНИМ» или имя типа, специфического для источника данных.<br /><br /> Значение «ALIAS» и «СИНОНИМ» зависят от драйвера.|  
|"ПРИМЕЧАНИЯ" (ODBC 1.0)|5|Varchar|Описание таблицы.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода не позволяет освободить дескрипторы и подключения. См. в разделе [SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md) и [SQLFreeStmt, функция](../../../odbc/reference/syntax/sqlfreestmt-function.md) примеры кода для освобождения дескрипторов и инструкций.  
  
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
|Привязка к столбцу в результирующем наборе буфер|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращает привилегии для столбца или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Возврат столбцов в таблице или таблицах|[Функция SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Возврат статистики таблиц и индексов|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возвращает привилегии для таблицы или таблиц|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
