---
title: Функция S'LGetФункции (ru) Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15537b28ff2bae8a4fcd3e7be82426eb53aa83a8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285334"
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions, функция
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **SLGetFunctions** возвращает информацию о том, поддерживает ли драйвер определенную функцию ODBC. Эта функция реализована в менеджере драйвера; она также может быть реализована в драйверах. Если драйвер реализует **S'LGetFunctions,** менеджер драйвера вызывает функцию в драйвере. В противном случае он выполняет саму функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ПодключениеРучка*  
 [Input] Дескриптор подключения  
  
 *ФункцияId*  
 (Вход) **Значение #define,** которое определяет функцию интересов ODBC; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** используется приложением ODBC 3 *.x* для определения поддержки ODBC 3 *.x* и более ранних функций. **SQL_API_ALL_FUNCTIONS** используется приложением ODBC 2 *.x* для определения поддержки ODBC 2 *.x* и более ранних функций.  
  
 Для списка **#define** значений, которые определяют функции ODBC, см.  
  
 *ПоддерживаемыйPtr*  
 (Выход)  Если *FunctionId* идентифицирует единую функцию ODBC, *SupportedPtr* указывает на одно значение S'LUSMALLINT, которое SQL_TRUE если указанная функция поддерживается драйвером, и SQL_FALSE, если она не поддерживается.  
  
 Если *FunctionId* SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* указывает на массив S'LSMALLINT с рядом элементов, равных SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Этот массив рассматривается менеджером драйверов как 4000-битная битовая карта, которая может быть использована для определения того, поддерживается ли функция ODBC 3 *.x* или более ранняя. Макрос SQL_FUNC_EXISTS называется для определения поддержки функций. (См. "Комментарии.") Приложение ODBC 3 *.x* может вызывать **S'LGetFunctions** с SQL_API_ODBC3_ALL_FUNCTIONS против драйвера ODBC 3 *.x* или ODBC 2 *.x.*  
  
 Если *FunctionId* SQL_API_ALL_FUNCTIONS, *SupportedPtr* указывает на массив S'LUSMALLINT из 100 элементов. Массив индексируется **#define** значениями, используемыми *FunctionId* для идентификации каждой функции ODBC; некоторые элементы массива не используются и зарезервированы для использования в будущем. Элемент SQL_TRUE если он идентифицирует функцию ODBC 2 *.x* или более раннюю функцию, поддерживаемую драйвером. Это SQL_FALSE если он определяет функцию ODBC, не поддерживаемую драйвером, или не идентифицирует функцию ODBC.  
  
 Массивы, возвращенные в*функции «SupportedPtr»,* используют нулевую индексацию.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetFunctions** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью HandleType* SQL_HANDLE_DBC и *ручки* *ConnectionHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LGetFunctions,** и разъясняются каждые из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------|-----|-----------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **S'LGetФункции** были вызваны до **S'LConnect**, **S'LBrowseConnect**, или **S'LDriverConnect**.<br /><br /> (DM) **S'LBrowseConnect** был вызван для *ConnectionHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до того, как **s'LBrowseConnect** вернулся SQL_SUCCESS_WITH_INFO или SQL_SUCCESS.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *ConnectionHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY095|Тип функции вне диапазона|(DM) Было указано значение *недействительного FunctionId.*|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
  
## <a name="comments"></a>Комментарии  
 **SLGetФункции** всегда возвращает, что **S'LGetФункции**, **S'LDataSources**, и **S'LDrivers** поддерживаются. Это происходит потому, что эти функции реализованы в менеджере драйвера. Менеджер драйвера сопоставит функцию ANSI с соответствующей функцией Unicode, если функция Unicode существует, и отобразит функцию Unicode с соответствующей функцией ANSI, если функция ANSI существует. Для получения информации о том, [Interface Conformance Levels](../../../odbc/reference/develop-app/interface-conformance-levels.md)как приложения используют **S'LGetФункции,** см.  
  
 Ниже приводится список действительных значений для *FunctionId* для функций, которые соответствуют уровню соответствия стандартам ISO 92:  
  
|Функциональное значение|Функциональное значение|  
|----------|----------|  
|SQL_API_SQLALLOCHANDLE|SQL_API_SQLGETDESCFIELD|  
|SQL_API_SQLBINDCOL|SQL_API_SQLGETDESCREC|  
|SQL_API_SQLCANCEL|SQL_API_SQLGETDIAGFIELD|  
|SQL_API_SQLCLOSECURSOR|SQL_API_SQLGETDIAGREC|  
|SQL_API_SQLCOLATTRIBUTE|SQL_API_SQLGETENVATTR|  
|SQL_API_SQLCONNECT|SQL_API_SQLGETFUNCTIONS|  
|SQL_API_SQLCOPYDESC|SQL_API_SQLGETINFO|  
|SQL_API_SQLDATASOURCES|SQL_API_SQLGETSTMTATTR|  
|SQL_API_SQLDESCRIBECOL|SQL_API_SQLGETTYPEINFO|  
|SQL_API_SQLDISCONNECT|SQL_API_SQLNUMRESULTCOLS|  
|SQL_API_SQLDRIVERS|SQL_API_SQLPARAMDATA|  
|SQL_API_SQLENDTRAN|SQL_API_SQLPREPARE|  
|SQL_API_SQLEXECDIRECT|SQL_API_SQLPUTDATA|  
|SQL_API_SQLEXECUTE|SQL_API_SQLROWCOUNT|  
|SQL_API_SQLFETCH|SQL_API_SQLSETCONNECTATTR|  
|SQL_API_SQLFETCHSCROLL|SQL_API_SQLSETCURSORNAME|  
|SQL_API_SQLFREEHANDLE|SQL_API_SQLSETDESCFIELD|  
|SQL_API_SQLFREESTMT|SQL_API_SQLSETDESCREC|  
|SQL_API_SQLGETCONNECTATTR|SQL_API_SQLSETENVATTR|  
|SQL_API_SQLGETCURSORNAME|SQL_API_SQLSETSTMTATTR|  
|SQL_API_SQLGETDATA| |  
  
 Ниже приводится список действительных значений для *FunctionId* для функций, соответствующих уровню соответствия стандартам Open Group:  
  
|Функциональное значение|Функциональное значение|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Ниже приводится список действительных значений для *FunctionId* для функций, соответствующих уровню соответствия стандартам ODBC.  
  
|Функциональное значение|Функциональное значение|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 При работе с драйвером ODBC 2 *.x,* **S'LBulkOperations** будет возвращен атакжем поддержкой только в том случае, если оба из следующих верны: драйвер ODBC 2 *.x* поддерживает **S'LSetPos,** а тип информации SQL_POS_OPERATIONS возвращает SQL_POS_ADD бит как набор.  
  
 Ниже приведен список действительных значений для *FunctionId* для функций, введенных в ODBC 3.8 или позже:  
  
|Функциональное значение|  
|-|  
|SQL_API_SQLCANCELHANDLE|  
  
 **S'LКансканхальд** будет возвращен в качестве поддержки только в том случае, если драйвер поддерживает как **S'LCancel,** так и **S'LКансандер.** Если **S'LCancel** поддерживается, а **s'LCancelHandle** нет, приложение все равно может вызвать **S'LCancelHandle** на ручке оператора, потому что оно будет отображено на **s'LCancel**.  
  
## <a name="sql_func_exists-macro"></a>SQL_FUNC_EXISTS Макро  
 Макрос SQL_FUNC_EXISTS *(SupportedPtr*, *FunctionID)* используется для определения поддержки ODBC 3 *.x* или более ранних функций после того, как **S'LGetFunctions** был вызван с аргументом *FunctionId* SQL_API_ODBC3_ALL_FUNCTIONS. Приложение вызывает SQL_FUNC_EXISTS с аргументом *SupportedPtr,* установленным на *SupportedPtr,* передаваемым в *S'LGetFunctions,* и с аргументом *FunctionID,* установленным для **#define** для функции. SQL_FUNC_EXISTS возвращаетSQL_TRUE если функция поддерживается, и SQL_FALSE иным образом.  
  
> [!NOTE]
>  При работе с драйвером ODBC 2 *.x,* менеджер драйвера ODBC 3 *.x* вернется SQL_TRUE для **S'LAllocHandle** и **SQLFreeStmt** **S'LFreeHandle,** потому **SQLFreeConnect**что **S'LAllocHandle** отображается на карте **SQLFreeEnv**на **S'LAllocEnv**, **S'LAllocConnect**, или **S'LAllocStMT**, и потому, что **S'LFree** SQL_HANDLE_DESC **Тем** не **SQLFreeHandle** менее, несмотря *HandleType* на то, что SQL_TRUE возвращается для функций, не имеется функции ODBC 2 *.x,* на которые можно отнести карту.  
  
## <a name="code-example"></a>Пример кода  
 Следующие три примера показывают, как приложение использует **S'LGetFunctions,** чтобы определить, поддерживает ли драйвер **S'LTables,** **S'LColumns**и **S'LStatistics.** Если драйвер не поддерживает эти функции, приложение отключается от драйвера. Первый пример вызывает **S'LGetФункции** один раз для каждой функции.  
  
```cpp  
SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
  
retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &TablesExists);  
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &ColumnsExists);  
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &StatisticsExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (retcodeTables == SQL_SUCCESS && TablesExists == SQL_TRUE &&   
retcodeColumns == SQL_SUCCESS && ColumnsExists == SQL_TRUE &&   
retcodeStatistics == SQL_SUCCESS && StatisticsExists == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Во втором примере приложение ODBC 3.x вызывает **s'LGetFunctions** и передает ему массив, в котором **S'LGetFunctions** возвращает информацию обо всех функциях ODBC 3.x и более ранних функциях.  
  
```cpp  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (reccode == SQL_SUCCESS &&   
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Третьим примером является приложение ODBC 2.x, которое вызывает **S'LGetFunctions** и передает ему массив из 100 элементов, в которых **S'LGetFunctions** возвращает информацию обо всех функциях ODBC 2.x и более ранних функциях.  
  
```cpp  
#define FUNCTIONS 100  
  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[FUNCTIONS];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);  
  
/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */  
if (retcode == SQL_SUCCESS &&   
fExists[SQL_API_SQLTABLES] == SQL_TRUE &&  
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &&  
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE)   
{  
  
   /* Continue with application */  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращение параметра атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возвращение информации о драйвере или источнике данных|[SQLGetInfo, функция](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Возвращение атрибута оператора|[Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
