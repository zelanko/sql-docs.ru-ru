---
description: Функция SQLTables
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1eb095849362914074e2c1e7f02166db2712894
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421048"
---
# <a name="sqltables-function"></a>Функция SQLTables
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: открытая группа  
  
 **Сводка**  
 **SQLTables** возвращает список имен таблиц, каталогов или схем, а также табличных типов, хранящихся в определенном источнике данных. Драйвер возвращает сведения в виде результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
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
 *статеменсандле*  
 Входной Маркер инструкции для полученных результатов.  
  
 *CatalogName*  
 Входной Имя каталога. Аргумент *CatalogName* принимает шаблоны поиска, если SQL_OV_ODBC3 атрибут среды SQL_ODBC_VERSION; Он не принимает шаблоны поиска, если задан параметр SQL_OV_ODBC2. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("") указывает на таблицы, не имеющие каталогов.  
  
 Если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не важен. Если это SQL_FALSE, *CatalogName* является аргументом значения шаблона; он обрабатывается буквально, и его регистр важен. Дополнительные сведения см. [в разделе аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Входной Длина в символах **CatalogName*.  
  
 *SchemaName*  
 Входной Шаблон поиска строк для имен схем. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("") указывает на те таблицы, которые не имеют схем.  
  
 Если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_TRUE, то объект *SchemaName* рассматривается как идентификатор и его регистр не важен. Если это SQL_FALSE, то *SchemaName* является аргументом-шаблоном значения; он обрабатывается буквально, и его регистр важен.  
  
 *NameLength2*  
 Входной Длина в символах **SchemaName*.  
  
 *TableName*  
 Входной Шаблон поиска строки для имен таблиц.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не важен. Если это SQL_FALSE, *TableName* является аргументом значения шаблона; он обрабатывается буквально, и его регистр важен.  
  
 *NameLength3*  
 Входной Длина в символах **TableName*.  
  
 *TableType*  
 Входной Список типов таблиц для сопоставления.  
  
 Обратите внимание, что атрибут инструкции SQL_ATTR_METADATA_ID не влияет на аргумент *TableType* . *TableType* — это аргумент списка значений, независимо от значения параметра SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 Входной Длина в символах **TableType*.  
  
## <a name="returns"></a>Возвращаемое значение  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLTables** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLTables** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|24 000|Недопустимое состояние курсора|В *статеменсандле*был открыт курсор, а также был вызван **SQLFetch** или **SQLFetchScroll** . Эта ошибка возвращается диспетчером драйверов, если **SQLFetch** или **SQLFetchScroll** не вернул SQL_NO_DATA и возвращается драйвером, если **SQLFetch** или **SQLFetchScroll** вернул SQL_NO_DATA.<br /><br /> В *статеменсандле*был открыт курсор, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Выполнен откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Неизвестное завершение инструкции|Не удалось выполнить связанное соединение во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \* MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*. Затем функция была вызвана в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY009|Недопустимое использование пустого указателя|Атрибуту инструкции SQL_ATTR_METADATA_ID было присвоено значение SQL_TRUE, аргумент *CatalogName* был пустым указателем, а SQL_CATALOG_NAME *инфотипе* возвращает, что эти имена каталогов поддерживаются.<br /><br /> (DM) атрибуту инструкции SQL_ATTR_METADATA_ID было присвоено значение SQL_TRUE, а аргумент *SchemaName* или *TableName* — пустой указатель.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове SQLTables.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длины меньше 0, но не равно SQL_NTS.<br /><br /> Значение одного из аргументов длины имени превышает максимальную длину для соответствующего имени.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательная функция не реализована|Указан каталог, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Указана схема, и драйвер или источник данных не поддерживают схемы.<br /><br /> Для имени каталога, схемы таблицы или имени таблицы указан шаблон поиска строки, а источник данных не поддерживает шаблоны поиска для одного или нескольких этих аргументов.<br /><br /> Сочетание текущих параметров атрибутов SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживалось драйвером или источником данных.<br /><br /> Атрибуту инструкции SQL_ATTR_USE_BOOKMARKS было присвоено значение SQL_UB_VARIABLE, а атрибуту инструкции SQL_ATTR_CURSOR_TYPE задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло до того, как источник данных вернул запрошенный результирующий набор. Период ожидания задается через **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
## <a name="comments"></a>Комментарии  
 **SQLTables** перечисляет все таблицы в запрошенном диапазоне. Пользователь может или не иметь привилегий SELECT для любой из этих таблиц. Для проверки специальных возможностей приложение может:  
  
-   Вызовите **SQLGetInfo** и проверьте тип сведений SQL_ACCESSIBLE_TABLES.  
  
-   Вызовите **SQLTablePrivileges** , чтобы проверить права доступа для каждой таблицы.  
  
 В противном случае приложение должно иметь возможность обрабатывать ситуацию, когда пользователь выбирает таблицу, для которой не предоставлены привилегии **SELECT** .  
  
 Аргументы *SchemaName* и *TableName* принимают шаблоны поиска. Аргумент *CatalogName* принимает шаблоны поиска, если SQL_OV_ODBC3 атрибут среды SQL_ODBC_VERSION; Он не принимает шаблоны поиска, если задан параметр SQL_OV_ODBC2. Если задан параметр SQL_OV_ODBC3, драйвер ODBC 3 *. x* потребует, чтобы символы-шаблоны в аргументе *CatalogName* были преобразованы в буквальном виде. Дополнительные сведения о допустимых шаблонах поиска см. в разделе [аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md).  
  
> [!NOTE]  
>  Дополнительные сведения об общем использовании, аргументах и возвращаемых данных функций каталога ODBC см. в разделе [функции каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Для поддержки перечисления каталогов, схем и табличных типов определена следующая особая семантика для аргументов *CatalogName*, *SchemaName*, *TableName*и *TableType* в **SQLTables**:  
  
-   Если *CatalogName* имеет SQL_ALL_CATALOGS и *SchemaName* и *TableName* являются пустыми строками, результирующий набор содержит список допустимых каталогов для источника данных. (Все столбцы, кроме столбца TABLE_CAT содержат значения NULL.)  
  
-   Если *SchemaName* имеет SQL_ALL_SCHEMAS и *CatalogName* и *TableName* являются пустыми строками, результирующий набор содержит список допустимых схем для источника данных. (Все столбцы, кроме столбца TABLE_SCHEM содержат значения NULL.)  
  
-   Если *TableType* имеет значение SQL_ALL_TABLE_TYPES и *CatalogName*, *SchemaName*и *TableName* являются пустыми строками, результирующий набор содержит список допустимых табличных типов для источника данных. (Все столбцы, кроме столбца TABLE_TYPE содержат значения NULL.)  
  
 Если *TableType* не является пустой строкой, он должен содержать список значений, разделенных запятыми, для интересующих типов. Каждое значение может быть заключено в одинарные кавычки (') или без кавычек, например таблица, представление или таблица, представление. Приложение всегда должно указывать табличный тип в верхнем регистре. драйвер должен преобразовать табличный тип в любой вариант, необходимый для источника данных. Если источник данных не поддерживает указанный табличный тип, **SQLTables** не возвращает никаких результатов для этого типа.  
  
 **SQLTables** возвращает результаты в виде стандартного результирующего набора, упорядоченного по TABLE_TYPE, TABLE_CAT, TABLE_SCHEM и table_name. Сведения об использовании этих сведений см. в разделе [использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Чтобы определить фактическую длину столбцов TABLE_CAT, TABLE_SCHEM и TABLE_NAME, приложение может вызвать **SQLGetInfo** с типами сведений SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN и SQL_MAX_TABLE_NAME_LEN.  
  
 Следующие столбцы были переименованы для ODBC 3 *. x*. Изменения имени столбца не влияют на обратную совместимость, так как приложения привязаны по номеру столбца.  
  
|Столбец ODBC 2,0|Столбец ODBC 3 *. x*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 В следующей таблице перечислены столбцы результирующего набора. Дополнительные столбцы, которые выходят за пределы столбца 5 (remarks), могут быть определены драйвером. Приложение должно получить доступ к столбцам, относящимся к драйверу, выполнив подсчет с конца результирующего набора вместо того, чтобы задавать явную порядковую точку. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1,0)|1|Varchar|Имя каталога; Значение NULL, если неприменимо к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, он возвращает пустую строку ("") для таблиц, не имеющих каталогов.|  
|TABLE_SCHEM (ODBC 1,0)|2|Varchar|Имя схемы; Значение NULL, если неприменимо к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, он возвращает пустую строку ("") для тех таблиц, которые не имеют схем.|  
|TABLE_NAME (ODBC 1,0)|3|Varchar|Имя таблицы.|  
|TABLE_TYPE (ODBC 1,0)|4|Varchar|Имя типа таблицы; одно из следующих: "Таблица", "представление", "СИСТЕМная таблица", "Глобальный ВРЕМЕНный", "локальный ВРЕМЕНный", "псевдоним", "синоним" или имя типа, зависящего от источника данных.<br /><br /> Значения "псевдоним" и "синоним" зависят от драйвера.|  
|ЗАМЕЧАНИЯ (ODBC 1,0)|5|Varchar|Описание таблицы.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода не освобождаются дескрипторы и соединения. Примеры кода для освобождения дескрипторов и инструкций см. в разделе [функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) и [Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md) .  
  
```cpp  
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
|Привязка буфера к столбцу в результирующем наборе|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение привилегий для столбца или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Возврат столбцов в таблице или таблицах|[Функция SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Выборка одной строки или блока данных в прямом направлении|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Выборка блока данных или прокрутка результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Возврат статистики и индексов таблицы|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возвращение привилегий для таблицы или таблиц|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
