---
title: Асинхронное выполнение (метод опроса) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d64874a4633e7bede14051d882925f633dadc36c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913829"
---
# <a name="asynchronous-execution-polling-method"></a>Асинхронное выполнение (метод опроса)
Перед ODBC 3.8 и пакета SDK Windows 7 асинхронные операции было разрешено только для функций с инструкциями. Дополнительные сведения см. в разделе **выполнения асинхронной операции инструкции**далее в этом разделе.  
  
 ODBC 3.8 в Windows 7 SDK появился асинхронное выполнение на операции, относящиеся к соединению. Дополнительные сведения см. в разделе **асинхронно выполнении операций соединения** подраздел, далее в этом разделе.  
  
 В Windows 7 SDK, для асинхронного инструкции или операций соединения приложения определить, что асинхронная операция была завершения с помощью метода опроса. Начиная с Windows 8 SDK, можно определить, что асинхронная операция завершена с помощью метода уведомления. Дополнительные сведения см. в разделе [асинхронное выполнение (метод уведомления)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 По умолчанию драйверы выполнять функции ODBC, синхронно. то есть приложение вызывает функцию, и драйвер не возвращает управление приложению до завершения выполнения функции. Тем не менее некоторые функции могут быть выполнены асинхронно; т. е приложение вызывает функцию, и драйвер, после обработки минимальный, возвращает управление приложению. Затем, при выполнении первой функции по-прежнему приложения могут вызывать другие функции.  
  
 Асинхронное выполнение поддерживается большинство функций, которые выполняются во многом в источнике данных, такие как функции для установления соединения, подготовки и выполнения инструкций SQL, получить метаданные, получения данных и фиксации транзакции. Это может пригодиться, если задача, выполняемая в источнике данных занимает много времени, например процесса входа в систему или сложный запрос с большими базами данных.  
  
 Когда приложение выполняет функции с помощью инструкции или соединения, настроенную для асинхронной обработки, драйвер выполняет минимальный объем обработки (например, при проверке аргументы для ошибок), передает обработку в источнике данных и возвращает Управление приложение с кодом возврата SQL_STILL_EXECUTING. Затем приложение выполняет другие задачи. Для определения момента завершения асинхронной функции, приложения путем вызова функции с теми же аргументами, как он изначально использовался опрашивает драйвер через регулярные интервалы. Если функция по-прежнему выполняется, он возвращает значение SQL_STILL_EXECUTING; Если завершения выполнения, он возвращает код, который оно было возвращено бы она выполнена синхронно, например SQL_SUCCESS, SQL_NEED_DATA или SQL_ERROR.  
  
 Является ли функция выполняется синхронно или асинхронно является подходящий драйвер. Предположим, например, метаданные результирующего набора, кэшированных в драйвере. В этом случае он занимает немного времени для выполнения **SQLDescribeCol** и драйвера следует просто выполняет эту функцию вместо искусственно задержка выполнения. С другой стороны Если этот драйвер должен для извлечения метаданных из источника данных, он должен возвращать элемент управления в приложение при его таким образом. Таким образом приложения должен быть способен обрабатывать код возврата от SQL_STILL_EXECUTING, если вначале выполняет функцию асинхронно.  
  
## <a name="executing-statement-operations-asynchronously"></a>Выполнение инструкции операции асинхронно  
 Следующие инструкции функции работают с источником данных и может выполняться асинхронно:  
  
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
  
 Выполнение асинхронных инструкций контролируется на каждой инструкции или на уровне отдельного подключения, в зависимости от источника данных. То есть приложение не указывает определенную функцию должен выполняться асинхронно, но любая функция выполнения на определенной инструкции находится асинхронное выполнение. Чтобы найти out, какой из них поддерживается, приложение вызывает [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) с параметром SQL_ASYNC_MODE. SQL_AM_CONNECTION возвращается в том случае, если поддерживается асинхронное выполнение уровня соединения (для дескриптора инструкции); SQL_AM_STATEMENT, если поддерживается асинхронное выполнение на уровне инструкций.  
  
 Чтобы указать, что функций, выполняемых с определенной инструкции должны быть выполнен асинхронно, приложение вызывает **SQLSetStmtAttr** атрибуту SQL_ATTR_ASYNC_ENABLE атрибута и назначает ей значение SQL_ASYNC_ENABLE_ON. Если поддерживается асинхронной обработки на уровне соединения, атрибут инструкции атрибуту SQL_ATTR_ASYNC_ENABLE доступно только для чтения, и его значение совпадает со значением атрибута соединения, на котором была выделена инструкция соединения. Это специфические для драйвера, задано ли значение атрибута инструкции во время выделения инструкции или более поздней версии. Попытка задать его вернет значение SQL_ERROR и SQLSTATE HYC00 (дополнительная возможность не реализована).  
  
 Чтобы указать, функций, выполняемых с определенного соединения должны быть выполнен асинхронно, приложение вызывает **SQLSetConnectAttr** атрибуту SQL_ATTR_ASYNC_ENABLE атрибута и назначает ей значение SQL_ASYNC_ENABLE_ON. Все дескрипторы инструкции в будущем, выделенные при соединении будет включена для асинхронного выполнения; это определяемые драйвером существующего дескриптора инструкции будут использоваться при выполнении этого действия. Если атрибуту SQL_ATTR_ASYNC_ENABLE SQL_ASYNC_ENABLE_OFF, все инструкции по соединению, в синхронном режиме. Если включено асинхронное выполнение, несмотря на отсутствие активного оператора в соединении, возвращается ошибка.  
  
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
  
 Пока функция асинхронно, приложение может вызывать функции любыми другими операторами. Приложение также может вызывать функции в любые соединения, за исключением того, связанные с асинхронной инструкцией. Но приложение можно вызвать только исходную функцию и следующие функции (с дескриптором инструкции или соединения, дескриптор среды), после операции инструкция возвращает значение SQL_STILL_EXECUTING.  
  
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
  
 Если приложение вызывает любой другой функции с асинхронной инструкции или соединения, связанного с этой инструкции, то функция возвращает SQLSTATE HY010 (функция ошибка последовательности), например.  
  
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
  
 Когда приложение вызывает функцию, чтобы определить, является ли она все еще выполняется асинхронно, он должен использовать исходный дескриптор инструкции. Это так, как асинхронное выполнение отслеживается отдельно для каждой инструкции. Приложение также необходимо указать допустимые значения для остальных аргументов — будет выполнять аргументы исходного — обходят ошибки проверки диспетчера драйверов. Однако после драйвер проверяет дескриптора инструкции и определяет, что инструкция выполняется асинхронно, игнорирует все аргументы.  
  
 Во время выполнения функция асинхронно — то есть после возвращения SQL_STILL_EXECUTING и перед возвращает другой код, приложение можно отменить, вызвав **SQLCancel** или **SQLCancelHandle** с тем же дескриптором инструкции. Это не гарантируется для отмены выполнения функции. Например функция может уже завершено. Кроме того, код, возвращенный **SQLCancel** или **SQLCancelHandle** определяет только то, успешно ли выполнено попытка ее отмены функции, не ли его отменить фактически функция. Чтобы определить, была ли отменена функцию, приложение вызывает функцию еще раз. Если функция была отменена, он возвращает значение SQL_ERROR и SQLSTATE HY008 (операция отменена). Если функция не была отменена, она возвращает другой код, например SQL_SUCCESS, SQL_STILL_EXECUTING или SQL_ERROR с разных SQLSTATE.  
  
 Если драйвер поддерживает асинхронной обработки на уровне инструкции, приложение вызывает отключение асинхронное выполнение определенной инструкции **SQLSetStmtAttr** атрибуту SQL_ATTR_ASYNC_ENABLE атрибута и назначает ей SQL_ ASYNC_ENABLE_OFF. Если драйвер поддерживает асинхронной обработки на уровне соединения, приложение вызывает **SQLSetConnectAttr** чтобы выставить атрибуту SQL_ATTR_ASYNC_ENABLE значение SQL_ASYNC_ENABLE_OFF, который отключает асинхронное выполнение всех инструкций на соединение.  
  
 Приложение должно обрабатывать диагностические записи в цикле повторяющейся исходной функции. Если **SQLGetDiagField** или **SQLGetDiagRec** вызывается при выполнении асинхронной функции, он вернет текущий список диагностических записей. Каждый раз, когда исходный вызов функции будет повторяться, очищает предыдущие диагностических записей.  
  
## <a name="executing-connection-operations-asynchronously"></a>Асинхронное выполнение операций соединения  
 Перед ODBC 3.8 была разрешена асинхронное выполнение операций, связанных с инструкции, такие как подготовки, выполнения и выборки, а также как для операций с метаданными каталога. Начиная с ODBC 3.8, асинхронное выполнение можно также для операций, связанных с соединения, например, подключение, отключение, commit и rollback.  
  
 Дополнительные сведения об ODBC 3.8 см. в разделе [новые возможности ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 Асинхронное выполнение операций соединения можно использовать в следующих случаях:  
  
-   Когда небольшое количество потоков управляет большое количество устройств с очень высокой скорости. С целью повышения скорости реагирования и масштабируемости рекомендуется для всех операций в асинхронный.  
  
-   Если вы хотите перекрывать операций базы данных на несколько соединений для сокращения времени, затраченного передачи.  
  
-   Эффективный асинхронные вызовы ODBC и возможность отмены операций соединения позволяют приложению разрешить пользователю отмените медленно операции, не дожидаясь времени ожидания для.  
  
 Следующие функции, которые работают на дескрипторов соединений, теперь могут быть выполнены асинхронно:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Чтобы определить, поддерживает ли драйвер асинхронные операции для этих функций, приложение вызывает **SQLGetInfo** с SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE возвращается в том случае, если асинхронные операции поддерживаются. SQL_ASYNC_DBC_NOT_CAPABLE возвращается в том случае, если асинхронные операции не поддерживаются.  
  
 Чтобы указать, функций, выполняемых с определенного соединения должны быть выполнен асинхронно, приложение вызывает **SQLSetConnectAttr** и устанавливает параметр SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE атрибут SQL_ASYNC_DBC_ENABLE МАКРОСОВ. С помощью атрибута соединения перед установлением соединения всегда выполняется синхронно. Кроме того, операции, указание соединений атрибута параметр SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE с **SQLSetConnectAttr** всегда выполняется синхронно.  
  
 Приложение можно включить асинхронную операцию до соединения. Поскольку диспетчер драйверов не удается определить драйвер до соединения, диспетчер драйверов всегда будет возвращать успеха в **SQLSetConnectAttr**. Тем не менее он не сможет подключиться, если драйвер ODBC не поддерживает асинхронные операции.  
  
 Как правило может существовать максимум один асинхронное выполнение функции, связанной с дескриптора определенного соединения или дескриптора инструкции. Однако дескриптора соединения может иметь более одного связанного дескриптора. Если ни одна асинхронная операция выполняется в этом дескрипторе соединения, дескриптор соответствующий оператор может выполнения асинхронной операции. Аналогичным образом может быть асинхронной операции на дескрипторе соединений нет асинхронных операций в данный момент дескриптором любые связанные инструкции. Попытка выполнить асинхронную операцию, используя дескриптор, который в данный момент выполняется асинхронная операция вернет HY010 «Ошибочная последовательность функций».  
  
 Если операция соединения возвращает значение SQL_STILL_EXECUTING, приложение может только вызвать исходную функцию и следующие функции для этого дескриптора соединения:  
  
-   **SQLCancelHandle** (в этом дескрипторе соединения)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (распределение ENV/DBC)  
  
-   **SQLAllocHandleStd** (распределение ENV/DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Приложение должно обрабатывать диагностические записи в цикле повторяющейся исходной функции. Если SQLGetDiagField или SQLGetDiagRec вызывается при выполнении асинхронной функции, возвращается текущий список диагностических записей. Каждый раз, когда исходный вызов функции будет повторяться, очищает предыдущие диагностических записей.  
  
 Если соединение выполняется открытии или закрытии асинхронно, операция будет завершена, когда приложение получает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO в первоначальном вызове функции.  
  
 Добавлена новая функция ODBC 3.8 **SQLCancelHandle**. Эта функция отменяет функции шесть соединений (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**, и **SQLSetConnectAttr**). Приложение должно вызывать **SQLGetFunctions** , чтобы определить, поддерживает ли драйвер **SQLCancelHandle**. Как и в **SQLCancel**, если **SQLCancelHandle** завершается успешно, это не значит, операция была отменена. Приложение должно вызывать исходную функцию еще раз, чтобы определить, если операция была отменена. **SQLCancelHandle** позволяет отменить асинхронные операции для дескрипторов соединения или дескрипторы инструкций. С помощью **SQLCancelHandle** для отмены операции в операторе дескриптор является вызовом **SQLCancel**.  
  
 Нет необходимости поддерживать протоколы **SQLCancelHandle** и асинхронное подключение операций одновременно. Драйвер может поддерживать операции асинхронное подключение, но не **SQLCancelHandle**, или наоборот.  
  
 Операции асинхронное подключение и **SQLCancelHandle** также может использоваться с ODBC 3.x и ODBC 2.x приложений с помощью драйвера ODBC 3.8 и диспетчер драйверов ODBC 3.8. Сведения о включении старые приложения для использования новых возможностей в более поздней версии ODBC см. в разделе [Матрица совместимости](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Организация пулов соединений  
 Каждый раз, когда пул подключений включен, асинхронные операции поддерживаются только как минимум для установления подключения (с **SQLConnect** и **SQLDriverConnect**) и закрывает соединение с **SQLDisconnect**. Но приложение по-прежнему должен быть способен обрабатывать SQL_STILL_EXECUTING возвращаемое значение **SQLConnect**, **SQLDriverConnect**, и **SQLDisconnect**.  
  
 Если включен пул соединений, **SQLEndTran** и **SQLSetConnectAttr** поддерживаются для асинхронных операций.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показано, как использовать **SQLSetConnectAttr** по включению асинхронного выполнения для функции, относящиеся к соединению.  
  
### <a name="code"></a>код  
  
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
 В этом примере показаны операции асинхронной фиксации. Операции отмены также могут быть выполнены таким образом.  
  
### <a name="code"></a>код  
  
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
