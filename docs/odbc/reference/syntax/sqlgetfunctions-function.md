---
title: "Функция SQLGetFunctions | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLGetFunctions
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetFunctions
helpviewer_keywords: SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 192eab3f4d34cd00bd4d3a0d257d8a941e82c456
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions, функция
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetFunctions** возвращает сведения о том, поддерживает ли драйвер определенной функции ODBC. Эта функция реализована в диспетчере драйвера. Он также может осуществляться в драйверах. Если драйвер реализует **SQLGetFunctions**, диспетчер драйверов вызывает функцию в драйвере. В противном случае он выполняет самой функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConnectionHandle*  
 [Вход] Дескриптор соединения.  
  
 *Идентификатор FunctionId*  
 [Вход] Объект **#define** значение, определяющее функции ODBC интерес; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** используется ODBC 3*.x* приложения для определения поддержки ODBC 3*.x* и более ранних функции. **SQL_API_ALL_FUNCTIONS** используется ODBC 2*.x* приложения для определения поддержки ODBC 2*.x* и более ранних функции.  
  
 Список **#define** значения, которые определяют функции ODBC см. в таблицах в «Комментарии».  
  
 *SupportedPtr*  
 [Выход]  Если *FunctionId* определяет одну функцию ODBC, *SupportedPtr* точек должен быть единственным SQLUSMALLINT значение SQL_TRUE Если указанная функция поддерживается драйвером и SQL_FALSE, если это не так поддерживается.  
  
 Если *FunctionId* — SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* указывает на массив SQLSMALLINT с количеством элементов, равным SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Этот массив обрабатываются диспетчером драйверов как 4000 разрядную битовую карту, который может использоваться для определения, является ли ODBC 3*.x* или более ранней функция поддерживается. Макрос SQL_FUNC_EXISTS вызывается для определения функции поддержки. (В разделе «Комментарии».) ODBC 3*.x* приложение может вызвать **SQLGetFunctions** с SQL_API_ODBC3_ALL_FUNCTIONS для ODBC 3*.x* или ODBC 2*.x* драйвер.  
  
 Если *FunctionId* — SQL_API_ALL_FUNCTIONS, *SupportedPtr* указывает на массив SQLUSMALLINT 100 элементов. Массив индексируется по **#define** значений, используемых в *FunctionId* для идентификации каждой функции ODBC; некоторые элементы массива используется и зарезервировано для будущего использования. Элемент представляет собой SQL_TRUE, если он определяет ODBC 2*.x* или более ранней функции, поддерживаемые драйвером. Если он идентифицирует функция ODBC не поддерживается драйвером или не может определить функции ODBC не SQL_FALSE.  
  
 Массивы, возвращаемые в **SupportedPtr* использовать индексацию с нуля.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetFunctions** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_DBC и *обработки* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetFunctions** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------|-----|-----------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLGetFunctions** был вызван перед **SQLConnect**, **SQLBrowseConnect**, или **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** был вызван для *ConnectionHandle* и возвращается значение SQL_NEED_DATA. Эта функция была вызвана до **SQLBrowseConnect** возвращается SQL_SUCCESS_WITH_INFO или SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *ConnectionHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY095|Тип функции за пределами допустимого диапазона|(DM) недопустимый *FunctionId* было указано значение.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetFunctions** , всегда возвращает **SQLGetFunctions**, **SQLDataSources**, и **SQLDrivers** поддерживаются. Это делается потому, что эти функции реализованы в диспетчера драйверов. Диспетчер драйверов будут сопоставляться функцию ANSI соответствующей функции Юникода, если существует функция Юникода и сопоставит функции Юникода с соответствующей функции ANSI, если существует функция ANSI. Дополнительные сведения об использовании приложений **SQLGetFunctions**, в разделе [уровни соответствия интерфейс](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, которые соответствуют уровню — соответствия стандартам ISO-92:  
  
|Значение FunctionId|Значение FunctionId|  
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
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, соответствующий требованиям к уровню соответствия стандартам — Open Group:  
  
|Значение FunctionId|Значение FunctionId|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, соответствующий уровню соответствия стандартам — ODBC.  
  
|Значение FunctionId|Значение FunctionId|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] при работе с ODBC 2*.x* драйвера, **SQLBulkOperations** будет возвращаться как поддерживается только значение true, если оба из следующих действий: ODBC 2*.x* драйвер поддерживает  **SQLSetPos**, и тип данных SQL_POS_OPERATIONS возвращает бит SQL_POS_ADD как набор.  
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, представленных в ODBC 3.8 или более поздней версии:  
  
|Значение FunctionId|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** будет возвращаться как поддерживается, только если драйвер поддерживает оба **SQLCancel** и **SQLCancelHandle**. Если **SQLCancel** поддерживается, но **SQLCancelHandle** — нет, приложение по-прежнему может вызвать **SQLCancelHandle** для дескриптора инструкции, потому что он будет сопоставлен  **SQLCancel**.  
  
## <a name="sqlfuncexists-macro"></a>Макрос SQL_FUNC_EXISTS  
 SQL_FUNC_EXISTS (*SupportedPtr*, *FunctionID*) макрос используется для определения поддержки ODBC 3*.x* или более ранней функций после **SQLGetFunctions**  был вызван с *FunctionId* аргумент SQL_API_ODBC3_ALL_FUNCTIONS. Приложение вызывает SQL_FUNC_EXISTS с *SupportedPtr* аргументу присвоено *SupportedPtr* переданный *SQLGetFunctions*и с  *Идентификатор FunctionID* аргументу присвоено **#define** для функции. SQL_FUNC_EXISTS в противном случае возвращает SQL_TRUE, если поддерживается функция and SQL_FALSE.  
  
> [!NOTE]  
>  При работе с ODBC 2*.x* драйвера ODBC 3*.x* диспетчера драйверов вернет SQL_TRUE для **SQLAllocHandle** и **SQLFreeHandle**из-за **SQLAllocHandle** сопоставляется **SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt**, и Поскольку **SQLFreeHandle** сопоставляется **SQLFreeEnv**, **SQLFreeConnect**, или **SQLFreeStmt**. **SQLAllocHandle** или **SQLFreeHandle** с *HandleType* аргумент SQL_HANDLE_DESC не поддерживается, однако несмотря на то, что SQL_TRUE возвращается для функций, так как нет ODBC 2*.x* функции для сопоставления в этом случае.  
  
## <a name="code-example"></a>Пример кода  
 В следующих трех примерах показано, как приложение использует **SQLGetFunctions** , чтобы определить, поддерживает ли драйвер **SQLTables**, **SQLColumns**, и  **SQLStatistics**. Если драйвер не поддерживает эти функции, приложение отключает от драйвера. В первом примере вызывается **SQLGetFunctions** один раз для каждой функции.  
  
```  
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
  
 Во втором примере вызывает приложение ODBC 3.x **SQLGetFunctions** и передает массив в котором **SQLGetFunctions** возвращает сведения обо всех ODBC 3.x и более ранних функции.  
  
```  
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
  
 В третьем примере представлен в приложении ODBC 2.x вызывает **SQLGetFunctions** и передает его массив из 100 элементов, в котором **SQLGetFunctions** возвращает сведения обо всех ODBC 2.x и более ранних функции.  
  
```  
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
|Возврат значения атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возврат сведений о драйверу или источнику данных|[Функция SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Возврат значения атрибута инструкции|[Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
