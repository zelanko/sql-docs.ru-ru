---
title: Асинхронное выполнение (метод опроса) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3200f4c83511f176c4d23af34f398a76047fe9a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701089"
---
# <a name="asynchronous-execution-polling-method"></a>Асинхронное выполнение (метод опроса)
Прежде чем ODBC 3.8 и пакет SDK Windows 7 асинхронные операции были разрешены только для функций с инструкциями. Дополнительные сведения см. в разделе **выполнение асинхронной операции инструкции**далее в этом разделе.  
  
 ODBC 3.8 в пакете SDK для Windows 7 появился асинхронное выполнение на операции, относящиеся к соединению. Дополнительные сведения см. в разделе **выполнение асинхронной операции подключения** разделе этой статьи.  
  
 В Windows 7 SDK, асинхронные инструкции или операций соединения приложения определить, что асинхронная операция была завершались с использованием метода опроса. Начиная с пакета SDK Windows 8, необходимо выяснить, что асинхронная операция завершена с помощью метода уведомления. Дополнительные сведения см. в разделе [асинхронное выполнение (метод уведомления)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 По умолчанию драйверы выполняются функции ODBC, синхронно. то есть приложение вызывает функцию, и драйвер не возвращает управление приложению до завершения выполнения функции. Тем не менее некоторые функции могут быть выполнены асинхронно; то есть приложение вызывает функцию, и драйвер, после минимальной обработки возвращает управление приложению. Приложение может повторно вызывать другие функции, пока первая функция по-прежнему выполняется.  
  
 Асинхронное выполнение поддерживается для большинства функций, которые выполняются во многом в источнике данных, такие как функции, устанавливать подключения, подготовки и выполнения инструкций SQL, получить метаданные, выборки данных и фиксации транзакции. Это наиболее полезно в тех случаях, когда задача, выполняемая в источнике данных занимает много времени, например, процесс входа в систему или сложного запроса в большую базу данных.  
  
 Когда приложение выполняет функции с помощью оператора или подключения, которая включена для асинхронной обработки, драйвер выполняет минимальный объем обработки (например, проверку аргументов для ошибок), передает обработку в источник данных и возвращает элемент управления в приложение с кодом возврата SQL_STILL_EXECUTING. Затем приложение выполняет другие задачи. Чтобы определить, при завершении асинхронной функции, приложение опрашивает драйвер с регулярными интервалами, вызвав функцию с аргументами, описанными его первоначально использовалась среда. Если функция по-прежнему выполняется, он возвращает значение SQL_STILL_EXECUTING; Если будет завершено его выполнение, он возвращает код, который она возвращала бы имели она выполнена синхронно, такие как SQL_SUCCESS, значение SQL_ERROR или SQL_NEED_DATA.  
  
 Ли функция выполняется синхронно или асинхронно — подходящий драйвер. Например предположим, метаданные результирующего набора, кэшируются в драйвере. В этом случае он занимает немного времени для выполнения **SQLDescribeCol** и должен просто выполнять функцию драйвер, а не искусственно задержать выполнение. С другой стороны Если этот драйвер должен получить метаданные из источника данных, он должен вернуть элемент управления в приложение во время его таким образом. Таким образом приложение необходимо иметь возможность обрабатывать код возврата отличен от SQL_STILL_EXECUTING, если вначале выполняет функции асинхронно.  
  
## <a name="executing-statement-operations-asynchronously"></a>Асинхронное выполнение инструкции операций  
 Следующие инструкции функции работают с источником данных и может исполняться асинхронно:  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 Выполнение асинхронных инструкций контролируется на соединению, в зависимости от источника данных либо в инструкции. То есть приложение не указывает, что определенную функцию для асинхронного выполнения, но что любой функция, выполненная для определенной инструкции для асинхронного выполнения. Чтобы найти out, какой из них поддерживается, приложение вызывает [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) с параметром SQL_ASYNC_MODE. SQL_AM_CONNECTION возвращается в том случае, если поддерживается уровня соединения асинхронное выполнение (для дескриптора инструкции); SQL_AM_STATEMENT, если поддерживается асинхронное выполнение на уровне инструкций.  
  
 Чтобы указать, что функций, выполняемых с определенной инструкции должны быть выполнен асинхронно, приложение вызывает **SQLSetStmtAttr** атрибуту SQL_ATTR_ASYNC_ENABLE атрибута и задает его значение SQL_ASYNC_ENABLE_ON. Если поддерживается асинхронная обработка уровня соединения, атрибуту SQL_ATTR_ASYNC_ENABLE атрибут инструкции только для чтения, и его значение совпадает со значением атрибута соединения подключения, где был выделен инструкцию. Это специфические для драйвера, задано ли значение атрибута инструкции во время выделения инструкции или более поздней версии. Попытка задать его вернет значение SQL_ERROR и SQLSTATE HYC00 (дополнительная возможность не реализована).  
  
 Чтобы указать, что функций, выполняемых с помощью определенного соединения должны быть выполнен асинхронно, приложение вызывает **SQLSetConnectAttr** атрибуту SQL_ATTR_ASYNC_ENABLE атрибута и задает его значение SQL_ASYNC_ENABLE_ON. Все дескрипторы будущих инструкции, выделенные при соединении, которые будут использоваться для асинхронного выполнения; это определенное драйвером включении существующего дескриптора инструкции этим действием. Если атрибуту SQL_ATTR_ASYNC_ENABLE SQL_ASYNC_ENABLE_OFF, все инструкции для подключения находятся в синхронном режиме. Если асинхронное выполнение включен во время активного оператора в соединении, возвращается ошибка.  
  
 Чтобы определить максимальное число активных параллельных инструкций в асинхронном режиме, драйвер может поддерживать в отдельном соединении, приложение вызывает **SQLGetInfo** с параметром SQL_MAX_ASYNC_CONCURRENT_STATEMENTS.  
  
 В следующем коде показано, как работает модель опроса:  
  
```  
SQLHSTMT  hstmt1;  
SQLRETURN rc;  
  
// Specify that the statement is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute a SELECT statement asynchronously.  
while ((rc=SQLExecDirect(hstmt1,"SELECT * FROM Orders",SQL_NTS))==SQL_STILL_EXECUTING) {  
   // While the statement is still executing, do something else.  
   // Do not use hstmt1, because it is being used asynchronously.  
}  
  
// When the statement has finished executing, retrieve the results.  
```  
  
 Пока функция выполняется асинхронно, приложение может вызвать функции, на каких-либо инструкций. Приложение также может вызывать функции для любого подключения, за исключением того, связанные с асинхронной инструкцией. Но приложение может вызывать только исходную функцию и следующие функции (с помощью дескриптора инструкции или подключения, дескриптор среды), после операции оператор возвращает значение SQL_STILL_EXECUTING.  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (для дескриптора инструкции)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Если приложение вызывает любой другой функции, с помощью асинхронного оператора, или с помощью соединения, связанного с этой инструкции, функция возвращает параметром SQLSTATE HY010 (функционировать ошибка последовательности), например.  
  
```  
SQLHDBC       hdbc1, hdbc2;  
SQLHSTMT      hstmt1, hstmt2, hstmt3;  
SQLCHAR *     SQLStatement = "SELECT * FROM Orders";  
SQLUINTEGER   InfoValue;  
SQLRETURN     rc;  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt2);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt3);  
  
// Specify that hstmt1 is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute hstmt1 asynchronously.  
while ((rc = SQLExecDirect(hstmt1, SQLStatement, SQL_NTS)) == SQL_STILL_EXECUTING) {  
   // The following calls return HY010 because the previous call to  
   // SQLExecDirect is still executing asynchronously on hstmt1. The  
   // first call uses hstmt1 and the second call uses hdbc1, on which  
   // hstmt1 is allocated.  
   SQLExecDirect(hstmt1, SQLStatement, SQL_NTS);   // Error!  
   SQLGetInfo(hdbc1, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // Error!  
  
   // The following calls do not return errors. They use a statement  
   // handle other than hstmt1 or a connection handle other than hdbc1.  
   SQLExecDirect(hstmt2, SQLStatement, SQL_NTS);   // OK  
   SQLTables(hstmt3, NULL, 0, NULL, 0, NULL, 0, NULL, 0);   // OK  
   SQLGetInfo(hdbc2, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // OK  
}  
```  
  
 Когда приложение вызывает функцию, чтобы определить, является ли он по-прежнему выполняется асинхронно, он должен использовать исходный дескриптор инструкции. Это обусловлено асинхронное выполнение отслеживается на основе инструкций. Приложение также необходимо указать допустимые значения для других аргументов — аргументы исходного сделает — для устранения ошибок диспетчера драйверов. Тем не менее после драйвер проверяет дескриптора инструкции и определяет, что инструкция выполняется асинхронно, он игнорирует все аргументы.  
  
 Пока функция выполняется асинхронно, то есть после ее возврата SQL_STILL_EXECUTING и перед возвращается другого кода, приложения можно отменить, вызвав **SQLCancel** или **SQLCancelHandle** с тем же дескриптором инструкции. Это не гарантируется для отмены выполнения функции. Например функция может уже завершена. Кроме того, код, возвращаемый методом **SQLCancel** или **SQLCancelHandle** только указывает, была ли попытка ее отмены функции в случае успешного выполнения, не ли она отменена фактически функции. Чтобы определить, отменена ли функция, приложение вызывает функцию еще раз. Если функция была отменена, она возвращает значение SQL_ERROR и SQLSTATE HY008 (операция отменена). Если функция не была отменена, она возвращает другим кодом, такие как SQL_SUCCESS, SQL_STILL_EXECUTING или SQL_ERROR с SQLSTATE другой.  
  
 Чтобы отключить асинхронное выполнение определенной инструкции, если драйвер поддерживает асинхронной обработки уровня инструкций, приложение вызывает **SQLSetStmtAttr** атрибуту SQL_ATTR_ASYNC_ENABLE атрибута и заменяет его на SQL_ ASYNC_ENABLE_OFF. Если драйвер поддерживает асинхронной обработки уровня соединения, приложение вызывает **SQLSetConnectAttr** чтобы выставить атрибуту SQL_ATTR_ASYNC_ENABLE значение SQL_ASYNC_ENABLE_OFF, который отключает асинхронное выполнение всех инструкций на подключение.  
  
 Приложение должно обрабатывать диагностических записей в цикле повторяющейся исходной функции. Если **SQLGetDiagField** или **SQLGetDiagRec** вызывается при выполнении асинхронной функции, он вернет текущий список диагностических записей. Каждый раз, когда с исходным вызовом функции выполняется повторно, он очищает предыдущих диагностических записей.  
  
## <a name="executing-connection-operations-asynchronously"></a>Асинхронное выполнение операций соединения  
 Прежде чем ODBC 3.8 асинхронное выполнение была разрешена для операции, относящиеся к инструкции, такие как подготовка, выполнения и выборки, а также как и для операций с метаданными каталога. Начиная с ODBC 3.8, асинхронное выполнение можно также для операций, относящиеся к соединению, например, подключение, отключение, commit и rollback.  
  
 Дополнительные сведения об ODBC 3.8, см. в разделе [новые возможности ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 Асинхронное выполнение операций соединения полезен в следующих сценариях:  
  
-   Когда несколько потоков управляет большое количество устройств с очень высокой скорости. Чтобы максимально увеличить время отклика и масштабируемость желательно все операции могут выполняться асинхронно.  
  
-   Если вы хотите перекрывать операций базы данных на несколько подключений для сокращения времени затраченного передачи.  
  
-   Эффективный асинхронные вызовы ODBC и возможность отмены операций соединения позволяют приложению разрешить пользователю отменить любые медленной операцией без ожидания для времени ожидания.  
  
 Следующие функции, которые работают на дескрипторов соединений, теперь могут быть выполнены асинхронно:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Чтобы определить, поддерживает ли драйвер асинхронных операций в этих функций, приложение вызывает **SQLGetInfo** с SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE возвращается в том случае, если поддерживаются асинхронные операции. SQL_ASYNC_DBC_NOT_CAPABLE возвращается в том случае, если асинхронные операции не поддерживаются.  
  
 Чтобы указать, что функций, выполняемых с помощью определенного соединения должны быть выполнен асинхронно, приложение вызывает **SQLSetConnectAttr** и устанавливает параметр SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE атрибут SQL_ASYNC_DBC_ENABLE В_КЛЮЧИТЬ. Присвоение атрибуту соединения перед установлением соединения всегда выполняется синхронно. Кроме того, операция, установка подключения атрибут параметр SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE с **SQLSetConnectAttr** всегда выполняется синхронно.  
  
 Приложения можно включить асинхронную операцию до соединения. Поскольку диспетчер драйверов не может определить, какой драйвер следует использовать до соединения, диспетчер драйверов всегда возвратит код успешного завершения в **SQLSetConnectAttr**. Тем не менее он не сможет подключиться, если драйвер ODBC не поддерживает асинхронные операции.  
  
 Как правило может существовать максимум один асинхронно выполнение функции, связанный с определенного соединения дескриптор или дескриптор инструкции. Тем не менее дескриптор соединения может иметь более одного дескриптора связанные инструкции. Если ни одна асинхронная операция, выполнение на дескриптор соединения, дескриптор соответствующий оператор может выполнения асинхронной операции. Аналогичным образом могут иметь асинхронной операции для дескриптора соединения, если нет асинхронных операций выполняется на любой дескриптор связанные инструкции. При попытке выполнить асинхронной операции, используя дескриптор, который в данный момент асинхронную операцию вернет HY010, «Ошибочная последовательность функций».  
  
 Если операции подключения возвращает SQL_STILL_EXECUTING, приложения можно вызывать только исходную функцию и следующие функции для этого дескриптора соединения:  
  
-   **SQLCancelHandle** (в этом дескрипторе соединения)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (с выделением ENV/DBC)  
  
-   **SQLAllocHandleStd** (с выделением ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Приложение должно обрабатывать диагностических записей в цикле повторяющейся исходной функции. Если SQLGetDiagField или SQLGetDiagRec вызывается при выполнении асинхронной функции, возвращается текущий список диагностических записей. Каждый раз, когда с исходным вызовом функции выполняется повторно, он очищает предыдущих диагностических записей.  
  
 Если соединение находится в процессе открытии или закрытии асинхронно, что операция завершена, когда приложение получает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO в исходном вызове функции.  
  
 Новая функция был добавлен ODBC 3.8, **SQLCancelHandle**. Эта функция отменяет функции шесть подключения (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**, и **SQLSetConnectAttr**). Приложение должно вызывать **SQLGetFunctions** чтобы определить, поддерживает ли драйвер **SQLCancelHandle**. Как и в **SQLCancel**, если **SQLCancelHandle** выполнилась успешно, это не значит, операция была отменена. Приложение должно вызывать исходную функцию еще раз, чтобы определить, если операция была отменена. **SQLCancelHandle** позволяет отменить асинхронные операции на дескрипторов соединений или дескрипторы инструкций. С помощью **SQLCancelHandle** для отмены операции в инструкции равносилен вызову метода является дескриптор **SQLCancel**.  
  
 Нет необходимости для поддержки обеих **SQLCancelHandle** и операции асинхронного подключения, в то же время. Драйвер может поддерживать операции асинхронного подключения, но не **SQLCancelHandle**, или наоборот.  
  
 Операции асинхронного подключения и **SQLCancelHandle** также может использоваться с ODBC 3.x и ODBC 2.x приложений с помощью драйвера ODBC 3.8 и диспетчер драйверов ODBC 3.8. Сведения о способах включения старое приложение для использования новых возможностей в более поздней версии ODBC, см. в разделе [Матрица совместимости](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Организация пулов соединений  
 Каждый раз, когда пул подключений включен, асинхронные операции поддерживаются только как минимум для установления соединения (с **SQLConnect** и **SQLDriverConnect**) и закрывает соединение с **SQLDisconnect**. Но приложения по-прежнему должны иметь возможность обрабатывать возвращаемое значение SQL_STILL_EXECUTING из **SQLConnect**, **SQLDriverConnect**, и **SQLDisconnect**.  
  
 Если включено использование пулов соединений, **SQLEndTran** и **SQLSetConnectAttr** поддерживаются для асинхронных операций.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показано, как использовать **SQLSetConnectAttr** по включению асинхронного выполнения для функции, относящиеся к соединению.  
  
### <a name="code"></a>Код  
  
```  
BOOL AsyncConnect (SQLHANDLE hdbc)   
{  
   SQLRETURN r;  
   SQLHANDLE hdbc;  
  
   // Enable asynchronous execution of connection functions.  
   // This must be executed synchronously, that is r != SQL_STILL_EXECUTING  
   r = SQLSetConnectAttr(  
         hdbc,   
         SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE,  
         reinterpret_cast<SQLPOINTER> (SQL_ASYNC_DBC_ENABLE_ON),  
         0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=AsyncDemo");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
  
   if (r == SQL_ERROR)   
   {  
      // Use SQLGetDiagRec to process the error.  
      // If SQLState is HY114, the driver does not support asynchronous execution.  
      return FALSE;  
   }  
  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion, with the same set of arguments.  
      r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   return TRUE;  
}  
  
```  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В этом примере показаны операции асинхронной фиксации. Откат операции также могут быть выполнены таким образом.  
  
### <a name="code"></a>Код  
  
```  
BOOL AsyncCommit ()   
{  
   SQLRETURN r;   
  
   // Assume that SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is SQL_ASYNC_DBC_ENABLE_ON.  
  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion with the same set of arguments.  
      r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкций (ODBC)](../../../odbc/reference/develop-app/executing-statements-odbc.md)
