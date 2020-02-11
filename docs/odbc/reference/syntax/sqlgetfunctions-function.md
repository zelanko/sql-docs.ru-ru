---
title: Функция SQLGetFunctions | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: edb58ebff212e494b84aed12397def2876d3728d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68345610"
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLGetFunctions** возвращает сведения о том, поддерживает ли драйвер определенную функцию ODBC. Эта функция реализована в диспетчере драйверов. его также можно реализовать в драйверах. Если драйвер реализует **SQLGetFunctions**, диспетчер драйверов вызывает функцию в драйвере. В противном случае он выполняет саму функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *коннектионхандле*  
 [Input] Дескриптор подключения  
  
 *FunctionId*  
 Входной Значение **#define** , определяющее интересующую функцию ODBC; **OrSQL_API_ALL_FUNCTIONS SQL_API_ODBC3_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** используется приложением ODBC 3 *. x* для определения поддержки функций ODBC 3 *. x* и более ранних версий. **SQL_API_ALL_FUNCTIONS** используется приложением ODBC 2 *. x* для определения поддержки функций ODBC 2 *. x* и более ранних версий.  
  
 Список значений **#define** , которые обозначают функции ODBC, см. в таблицах в комментариях.  
  
 *суппортедптр*  
 Проверки  Если параметр *FunctionId* определяет одну функцию ODBC, *суппортедптр* указывает на одно значение склусмаллинт, которое SQL_TRUE, если указанная функция поддерживается драйвером, и SQL_FALSE, если она не поддерживается.  
  
 Если параметр *FunctionId* имеет значение SQL_API_ODBC3_ALL_FUNCTIONS, *суппортедптр* указывает на массив SQLSMALLINT с числом элементов, равным SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Этот массив обрабатывается диспетчером драйверов как 4 000-разрядный точечный рисунок, который можно использовать для определения того, поддерживается ли функция ODBC 3 *. x* или более ранней версии. Для определения поддержки функций вызывается макрос SQL_FUNC_EXISTS. (См. раздел "Комментарии".) Приложение ODBC 3 *. x* может вызывать **SQLGetFunctions** с SQL_API_ODBC3_ALL_FUNCTIONS с драйвером ODBC 3 *. x* или ODBC 2 *. x* .  
  
 Если значение параметра *FunctionId* — SQL_API_ALL_FUNCTIONS, *СУППОРТЕДПТР* указывает на склусмаллинт массив элементов 100. Массив индексируется по **#define** значениям, используемым *FunctionId* для обнаружения каждой функции ODBC. Некоторые элементы массива не используются и зарезервированы для будущего использования. Элемент SQL_TRUE, если он определяет функцию ODBC 2 *. x* или более раннюю версию, поддерживаемую драйвером. Он SQL_FALSE, если он определяет функцию ODBC, не поддерживаемую драйвером, или не определяет функцию ODBC.  
  
 Массивы, возвращаемые в **суппортедптр* , используют индексацию, начинающуюся с нуля.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetFunctions** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_DBC и *маркером* *коннектионхандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLGetFunctions** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------|-----|-----------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) **SQLGetFunctions** был вызван до **SQLConnect**, **SQLBrowseConnect**или **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** был вызван для *коннектионхандле* и вернул SQL_NEED_DATA. Эта функция была вызвана до того, как **SQLBrowseConnect** вернул SQL_SUCCESS_WITH_INFO или SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *коннектионхандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY095|Тип функции вне допустимого диапазона|(DM) указано недопустимое значение *FunctionId* .|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetFunctions** всегда возвращает, что поддерживаются **SQLGetFunctions**, **SQLDataSources**и **SQLDrivers** . Это происходит потому, что эти функции реализуются в диспетчере драйверов. Диспетчер драйверов будет сопоставлять функцию ANSI с соответствующей функцией Юникода, если функция Юникода существует, и будет сопоставлять функцию Юникода с соответствующей функцией ANSI, если функция ANSI существует. Сведения о том, как приложения используют **SQLGetFunctions**, см. в разделе [уровни соответствия интерфейсов](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Ниже приведен список допустимых значений для параметра *FunctionId* для функций, которые соответствуют уровню соответствия стандартам ISO 92.  
  
|Значение параметра FunctionId|Значение параметра FunctionId|  
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
  
 Ниже приведен список допустимых значений для параметра *FunctionId* для функций, соответствующих уровню соответствия стандарту Open Group.  
  
|Значение параметра FunctionId|Значение параметра FunctionId|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Ниже приведен список допустимых значений для параметра *FunctionId* для функций, соответствующих уровню соответствия стандартам ODBC.  
  
|Значение параметра FunctionId|Значение параметра FunctionId|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] при работе с драйвером ODBC 2 *. x* **SQLBulkOperations** будет возвращен как поддерживаемый, только если выполняются оба следующих условия: драйвер ODBC 2 *. x* поддерживает функцию **SQLSetPos**, а тип информации SQL_POS_OPERATIONS возвращает SQL_POS_ADD бит как установленный.  
  
 Ниже приведен список допустимых значений для параметра *FunctionId* для функций, появившихся в ODBC 3,8 или более поздней версии.  
  
|Значение параметра FunctionId|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **склканцелхандле** будет возвращен как поддерживаемый, только если драйвер поддерживает как **SQLCancel** , так и **склканцелхандле**. Если **SQLCancel** поддерживается, но **склканцелхандле** — нет, приложение по-прежнему может вызвать **склканцелхандле** в обработчике инструкции, так как он будет сопоставлен с **SQLCancel**.  
  
## <a name="sql_func_exists-macro"></a>Макрос SQL_FUNC_EXISTS  
 Макрос SQL_FUNC_EXISTS (*суппортедптр*, *FunctionID*) используется для определения поддержки функций ODBC 3 *. x* или более ранних версий после вызова **SQLGetFunctions** с аргументом *FunctionID* SQL_API_ODBC3_ALL_FUNCTIONS. Приложение вызывает SQL_FUNC_EXISTS с аргументом *суппортедптр* , для которого задано значение *суппортедптр* , переданное в *SQLGetFunctions*, а аргумент *FunctionID* имеет значение **#define** для функции. SQL_FUNC_EXISTS возвращает SQL_TRUE, если функция поддерживается, и SQL_FALSE в противном случае.  
  
> [!NOTE]
>  При работе с драйвером ODBC 2 *. x* диспетчер драйверов ODBC 3 *. x* возвратит SQL_TRUE для **функцию SQLAllocHandle** и **SQLFreeHandle** , так как **функцию SQLAllocHandle** сопоставляется с **SQLAllocEnv**, **SQLAllocConnect**или **SQLAllocStmt**, а так как **SQLFreeHandle** сопоставляется с **SQLFreeEnv**, **SQLFreeConnect**или **SQLFreeStmt**. Однако **функцию SQLAllocHandle** или **SQLFreeHandle** с аргументом *параметром handletype* SQL_HANDLE_DESC не поддерживается, несмотря на то, что для функций возвращается SQL_TRUE, так как в данном случае отсутствует функция ODBC 2 *. x* для соответствия.  
  
## <a name="code-example"></a>Пример кода  
 В следующих трех примерах показано, как приложение использует **SQLGetFunctions** , чтобы определить, поддерживает ли драйвер **SQLTables**, **SQLColumns**и **SQLStatistics**. Если драйвер не поддерживает эти функции, приложение отключается от драйвера. Первый пример вызывает **SQLGetFunctions** один раз для каждой функции.  
  
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
  
 Во втором примере приложение ODBC 3. x вызывает **SQLGetFunctions** и передает ему массив, в котором **SQLGetFunctions** возвращает сведения обо всех функциях ODBC 3. x и более ранних версий.  
  
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
  
 В третьем примере приложение ODBC 2. x вызывает **SQLGetFunctions** и передает ему массив элементов 100, в котором **SQLGetFunctions** возвращает сведения обо всех функциях ODBC 2. x и более ранних версий.  
  
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
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Возврат значения атрибута соединения|[Функция SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Возврат сведений о драйвере или источнике данных|[SQLGetInfo, функция](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Возврат значения атрибута инструкции|[SQLGetStmtAttr, функция](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
