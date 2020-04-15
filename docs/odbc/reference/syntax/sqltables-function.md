---
title: Функция S'LTables Документы Майкрософт
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
ms.openlocfilehash: ae52e6431679ed0f260e6885090ac38363b4ef3d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287134"
---
# <a name="sqltables-function"></a>Функция SQLTables
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: Open Group  
  
 **Сводка**  
 **S'LTables** возвращает список имен таблицы, каталога или схемы и типов таблиц, хранящихся в определенном источнике данных. Водитель возвращает информацию в результате набора.  
  
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
 *Обработка заявления*  
 (Вход) Ручка оператора для извлеченных результатов.  
  
 *КаталогНайм*  
 (Вход) Название каталога. Аргумент *CatalogName* принимает шаблоны поиска, если атрибут среды SQL_ODBC_VERSION SQL_OV_ODBC3; он не принимает шаблоны поиска, если установлен SQL_OV_ODBC2. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер получает данные из разных DBMS, пустая строка (") указывает на те таблицы, которые не имеют каталогов.  
  
 Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *CatalogName* рассматривается как идентификатор, и его случай не является значительным. Если это SQL_FALSE, *CatalogName* является аргументом значения шаблона; к нему относятся буквально, и его случай имеет важное значение. Для получения дополнительной информации смотрите [аргументы в каталоге функции](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 (Вход) Длина в символах*каталогаName*.  
  
 *Schemaname*  
 (Вход) Шаблон поиска строк для имен схем. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер получает данные из различных DBMS, пустая строка (") указывает на те таблицы, которые не имеют схем.  
  
 Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *SchemaName* рассматривается как идентификатор и его случай не является значительным. Если это SQL_FALSE, *SchemaName* является аргументом значения шаблона; к нему относятся буквально, и его случай имеет важное значение.  
  
 *NameLength2*  
 (Вход) Длина в символах*SchemaName*.  
  
 *Tablename*  
 (Вход) Шаблон поиска строк для имен таблиц.  
  
 Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *TableName* рассматривается как идентификатор, и его случай не является значительным. Если это SQL_FALSE, *TableName* является аргументом значения шаблона; к нему относятся буквально, и его случай имеет важное значение.  
  
 *NameLength3*  
 (Вход) Длина в символах*таблицыName*.  
  
 *ТаблицаТип*  
 (Вход) Список типов таблиц для сопоставления.  
  
 Обратите внимание, что атрибут SQL_ATTR_METADATA_ID оператора не влияет на аргумент *TableType.* *TableType* — это аргумент списка значений, независимо от настройки SQL_ATTR_METADATA_ID.  
  
 *NameLength4*  
 (Вход) Длина в символах*таблицыType*.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LTables** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону s'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_STMT и *ручкой* *statementHandle.* В следующей таблице перечислены значения S'Lstate, обычно возвращаемые **S'LTables,** и приведены в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|24 000|Недопустимое состояние курсора|Курсор был открыт на *statementHandle*, и **S'LFetch** или **S'LFetchScroll** был вызван. Эта ошибка возвращается менеджером-драйвером, если **S'LFetch** или **S'LFetchScroll** не вернулись SQL_NO_DATA и возвращается водителем, если **S'LFetch** или **S'LFetchScroll** вернулся SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle,* но **S'LFetch** или **S'LFetchScroll** не были вызваны.|  
|40001|Сбой сериализации|Транзакция была отката из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Завершение заявления неизвестно|Связанное соединение сбой во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY009|Недействительное использование нулевой указатель|Атрибут SQL_ATTR_METADATA_ID оператора был установлен на SQL_TRUE, аргумент *CatalogName* был недействительным указателем, а SQL_CATALOG_NAME *InfoType* возвращает, что имена каталогов поддерживаются.<br /><br /> (DM) атрибут SQL_ATTR_METADATA_ID оператора был установлен на SQL_TRUE, а аргумент *SchemaName* или *TableName* был недействительным указателем.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась, когда был вызван S'LTables.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY090|Недействительная длина строки или буфера|(DM) Значение одного из аргументов длины было меньше, чем 0, но не равно SQL_NTS.<br /><br /> Значение одного из аргументов длины имени превысило значение максимальной длины соответствующего имени.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYC00|Дополнительная функция не реализована|Каталог был указан, и драйвер или источник данных не поддерживает каталоги.<br /><br /> Была указана схема, а драйвер или источник данных не поддерживает схемы.<br /><br /> Шаблон поиска строк был указан для имени каталога, схемы таблицы или названия таблицы, и источник данных не поддерживает шаблоны поиска для одного или нескольких из этих аргументов.<br /><br /> Комбинация текущих параметров атрибутов SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE оператора не была поддержана драйвером или источником данных.<br /><br /> Атрибут SQL_ATTR_USE_BOOKMARKS оператора был установлен на SQL_UB_VARIABLE, а атрибут SQL_ATTR_CURSOR_TYPE оператора был установлен на тип курсора, для которого водитель не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Период тайм-аута запроса истек до того, как источник данных вернул запрошенный набор результатов. Период тайм-аута устанавливается с **помощью S'LSetStmtAttr,** SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 **S'LTables** перечисляет все таблицы в запрашиваемом диапазоне. Пользователь может иметь или не иметь привилегий SELECT для любой из этих таблиц. Чтобы проверить доступность, приложение может:  
  
-   Позвоните по **телефону s'LGetInfo** и проверьте SQL_ACCESSIBLE_TABLES тип информации.  
  
-   Позвоните в **S'LTablePrivileges,** чтобы проверить привилегии для каждой таблицы.  
  
 В противном случае приложение должно быть в состоянии справиться с ситуацией, когда пользователь выбирает таблицу, для которой привилегии **SELECT** не предоставляются.  
  
 Аргументы *SchemaName* и *TableName* принимают шаблоны поиска. Аргумент *CatalogName* принимает шаблоны поиска, если атрибут среды SQL_ODBC_VERSION SQL_OV_ODBC3; он не принимает шаблоны поиска, если установлен SQL_OV_ODBC2. Если SQL_OV_ODBC3 установлен, водитель ODBC 3 *.x* потребует, чтобы символы подстановочных знаков в аргументе *CatalogName* были избеудены, чтобы лечиться буквально. Для получения дополнительной информации об [Pattern Value Arguments](../../../odbc/reference/develop-app/pattern-value-arguments.md)действительных шаблонах поиска см.  
  
> [!NOTE]  
>  Для получения дополнительной информации об общем использовании, аргументах и возвращенных данных функций каталога ODBC [см.](../../../odbc/reference/develop-app/catalog-functions.md)  
  
 Для поддержки перечисления каталогов, схем и типов таблиц, следующие специальные семантики определены для *CatalogName*, *SchemaName*, *TableName*, и *TableType* аргументы **S'LTables**:  
  
-   Если *CatalogueName* находится SQL_ALL_CATALOGS а *SchemaName* и *TableName* являются пустыми строками, набор результатов содержит список действительных каталогов для источника данных. (Все столбцы, кроме TABLE_CAT столбца, содержат NULLs.)  
  
-   Если *SchemaName* SQL_ALL_SCHEMAS а *CatalogueName* и *TableName* являются пустыми строками, набор результатов содержит список действительных схем для источника данных. (Все столбцы, кроме TABLE_SCHEM столбца содержат NULLs.)  
  
-   Если *TableType* SQL_ALL_TABLE_TYPES и *CatalogueName,* *SchemaName*и *TableName* являются пустыми строками, набор результатов содержит список действительных типов таблиц для источника данных. (Все столбцы, кроме TABLE_TYPE столбца содержат NULLs.)  
  
 Если *TableType* не является пустой строкой, он должен содержать список значений, разделенных запятой для типов интересов; каждое значение может быть заключено в отдельные кавычки (') или нецитируемые, например, 'TABLE', 'VIEW' или TABLE, VIEW. Приложение должно всегда указывать тип таблицы в верхнем регистре; водитель должен преобразовать тип таблицы в любой случай, необходимый источнику данных. Если источник данных не поддерживает определенный тип таблицы, **S'LTables** не возвращает результаты для этого типа.  
  
 **S'LTables** возвращает результаты в стандартный набор результатов, заказанный TABLE_TYPE, TABLE_CAT, TABLE_SCHEM и TABLE_NAME. Информацию о том, как эта информация может быть использована, можно узнать: [«Использование данных каталогов».](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
 Для определения фактической длины столбцов TABLE_CAT, TABLE_SCHEM и TABLE_NAME приложение может позвонить в **s'LGetInfo** с SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN и SQL_MAX_TABLE_NAME_LEN типами информации.  
  
 Следующие столбцы были переименованы в ODBC 3 *.x*. Изменения имени столбца не влияют на обратную совместимость, поскольку приложения связываются с номером столбца.  
  
|Колонка ODBC 2.0|Колонка ODBC 3 *.x*|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 В следующей таблице перечислены столбцы в наборе результатов. Дополнительные столбцы за пределами столбца 5 (REMARKS) могут быть определены драйвером. Приложение должно получить доступ к столбику, в зависимости от драйвера, отсчитывая от конца набора результатов вместо указания явного ординаторского положения. Для получения дополнительной информации смотрите [данные, возвращенные функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Название каталога; NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер получает данные из различных DBMS, он возвращает пустую строку ("") для тех таблиц, которые не имеют каталогов.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Название схемы; NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер получает данные из различных DBMS, он возвращает пустую строку ("") для тех таблиц, которые не имеют схем.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|Имя таблицы.|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|Имя типа таблицы; один из следующих: "TABLE", "VIEW", "SYSTEM TABLE", "GLOBAL TEMPORARY", "LOCAL TEMPORARY", "ALIAS", "SYNONYM", или имя конкретного типа источника данных.<br /><br /> Значения "ALIAS" и "SYNONYM" специфичны для водителей.|  
|ЗАМЕЧАНИЯ (ODBC 1.0)|5|Varchar|Описание таблицы.|  
  
## <a name="example"></a>Пример  
 Следующий пример кода не освобождает ручки и соединения. Для бесплатных ручек и инструкций с функциями [s'LFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md) и [S'LFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md) можно ознакомиться с функциями с кодом.  
  
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
|Привязка буфера к столбцовику в наборе результатов|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение привилегий для столбцов или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Возвращение столбцов в таблице или таблицах|[Функция SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|Получение одной строки или блока данных в направлении только вперед|[Функция S'LFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Получение блока данных или прокрутка набора результатов|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Статистика и индексы возвращающихся таблиц|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возвращение привилегий для таблицы или таблицы|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
