---
title: Функция SQLGetFunctions | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0a44320072f11a56b735502be3f1776f29cc1c0
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538022"
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions, функция
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetFunctions** возвращает сведения о том, поддерживает ли драйвер определенной функции ODBC. Эта функция реализуется в диспетчере драйверов. Он также может осуществляться в драйверах. Если драйвер реализует **SQLGetFunctions**, диспетчер драйверов вызывает функцию в драйвере. В противном случае он выполняет саму функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConnectionHandle*  
 [Вход] Дескриптор соединения.  
  
 *FunctionId*  
 [Вход] Объект **#define** значение, определяющее функции ODBC интерес; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** используется ODBC 3 *.x* приложения для определения поддержки ODBC 3 *.x* и более ранних функции. **SQL_API_ALL_FUNCTIONS** используется ODBC 2 *.x* приложения для определения поддержки ODBC 2 *.x* и более ранних функции.  
  
 Список **#define** значений, указывающих функции ODBC, см. в таблицах «Комментарии».  
  
 *SupportedPtr*  
 [Выход]  Если *FunctionId* определяет одну функцию ODBC, *SupportedPtr* точек в одном SQLUSMALLINT значение SQL_TRUE Если указанная функция поддерживается драйвером, и значение SQL_FALSE, если это не поддерживается.  
  
 Если *FunctionId* является SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* указывает на массив SQLSMALLINT с количеством элементов, равным SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Этот массив обрабатывается диспетчером драйверов как 4000 разрядный точечный рисунок, который может использоваться для определения ли ODBC 3 *.x* или поддерживается функция earlier. Макрос SQL_FUNC_EXISTS вызывается для определения функции поддержки. (См. в разделе «Комментарии».) ODBC 3 *.x* приложение может вызвать **SQLGetFunctions** с SQL_API_ODBC3_ALL_FUNCTIONS с ODBC 3 *.x* или ODBC 2 *.x* драйвер.  
  
 Если *FunctionId* является SQL_API_ALL_FUNCTIONS, *SupportedPtr* указывает на массив SQLUSMALLINT 100 элементов. Массив индексируется по **#define** значения, используемые свойством *FunctionId* для идентификации каждой функции ODBC; некоторые элементы массива являются используется и зарезервировано для использования в будущем. Элемент значение равно SQL_TRUE, если он определяет ODBC 2 *.x* или функция earlier, поддерживаемых драйвером. Это значение SQL_FALSE, если он определяет функцию ODBC, драйвер не поддерживает или не определяет функции ODBC.  
  
 Массивы, возвращаемые в **SupportedPtr* индексация с нуля.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetFunctions** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_DBC и *обрабатывать* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetFunctions** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------|-----|-----------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLGetFunctions** был вызван перед **SQLConnect**, **SQLBrowseConnect**, или **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** был вызван для *ConnectionHandle* и возвращается значение SQL_NEED_DATA. Эта функция была вызвана до **SQLBrowseConnect** возвращено значение SQL_SUCCESS_WITH_INFO или SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *ConnectionHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY095|Тип функции за пределами диапазона|(DM) указан недопустимый *FunctionId* было указано значение.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetFunctions** всегда возвращает, **SQLGetFunctions**, **SQLDataSources**, и **SQLDrivers** поддерживаются. Это делается потому, что эти функции реализованы в диспетчера драйверов. Диспетчер драйверов будут сопоставлены с соответствующей функции Юникода функцию ANSI, если функции Юникода существует и сопоставит функция Юникода с соответствующей функции ANSI, если существует функция ANSI. Сведения об использовании приложений **SQLGetFunctions**, см. в разделе [уровни соответствия интерфейса](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, которые соответствуют уровню соответствия стандартам ISO-92:  
  
|FunctionId значение|FunctionId значение|  
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
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, соответствующий требованиям к уровню соответствия стандартам Open Group:  
  
|FunctionId значение|FunctionId значение|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, соответствующий требованиям к уровню соответствия стандартам ODBC.  
  
|FunctionId значение|FunctionId значение|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] при работе с ODBC 2 *.x* драйвера, **SQLBulkOperations** будет возвращаться как поддерживаются только если оба из следующих условий: ODBC 2 *.x* драйвер поддерживает  **SQLSetPos**, и тип сведений SQL_POS_OPERATIONS возвращает бит SQL_POS_ADD как набор.  
  
 Ниже приведен список допустимых значений для *FunctionId* для функций, появившихся в ODBC 3.8 или более поздней версии:  
  
|FunctionId значение|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** будет возвращаться как поддерживаются, только если драйвер поддерживает оба **SQLCancel** и **SQLCancelHandle**. Если **SQLCancel** поддерживается, но **SQLCancelHandle** — нет, приложение по-прежнему может вызвать **SQLCancelHandle** для дескриптора инструкции, поскольку он будет сопоставлен с  **SQLCancel**.  
  
## <a name="sqlfuncexists-macro"></a>SQL_FUNC_EXISTS Macro  
 SQL_FUNC_EXISTS (*SupportedPtr*, *FunctionID*) макрос используется для определения поддержки ODBC 3 *.x* или более ранней функции после **SQLGetFunctions**  был вызван с *FunctionId* аргумент SQL_API_ODBC3_ALL_FUNCTIONS. Приложение вызывает SQL_FUNC_EXISTS с *SupportedPtr* аргумент значение *SupportedPtr* переданный *SQLGetFunctions*и с  *FunctionID* аргумент значение **#define** для функции. SQL_FUNC_EXISTS в противном случае возвращает SQL_TRUE, если поддерживается функция and SQL_FALSE.  
  
> [!NOTE]
>  При работе с ODBC 2 *.x* драйвера ODBC 3 *.x* диспетчера драйверов вернет SQL_TRUE для **SQLAllocHandle** и **SQLFreeHandle**поскольку **SQLAllocHandle** сопоставляется **SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt**, и так как **SQLFreeHandle** сопоставляется **SQLFreeEnv**, **SQLFreeConnect**, или **SQLFreeStmt**. **SQLAllocHandle** или **SQLFreeHandle** с *HandleType* аргумент SQL_HANDLE_DESC не поддерживается, тем не менее, несмотря на то, что SQL_TRUE возвращается для функций, так как нет ODBC 2 *.x* функции для сопоставления в этом случае.  
  
## <a name="code-example"></a>Пример кода  
 В следующих трех примерах показано, как приложение использует **SQLGetFunctions** чтобы определить, поддерживает ли драйвер **SQLTables**, **SQLColumns**, и  **SQLStatistics**. Если драйвер не поддерживает эти функции, приложение отключается от драйвера. В первом примере вызывается **SQLGetFunctions** один раз для каждой функции.  
  
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
  
 Во втором примере, вызывает в приложении ODBC 3.x **SQLGetFunctions** и передает массив в котором **SQLGetFunctions** возвращает сведения обо всех ODBC 3.x и более ранних функции.  
  
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
  
 Третий пример является вызывает в приложении ODBC 2.x **SQLGetFunctions** и передает его массив из 100 элементов, в котором **SQLGetFunctions** возвращает сведения обо всех ODBC 2.x и более ранних функции.  
  
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
|Возвращает значение атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возврат сведений о драйверу или источнику данных|[Функция SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Возвращает значение атрибута инструкции|[Функция SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
