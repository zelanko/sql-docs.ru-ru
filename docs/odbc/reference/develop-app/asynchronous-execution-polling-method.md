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
ms.openlocfilehash: 97fe8af6f02e9797bc14578edda09c420f8f94e2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077048"
---
# <a name="asynchronous-execution-polling-method"></a>Асинхронное выполнение (метод опроса)
До ODBC 3,8 и пакета SDK для Windows 7 асинхронные операции были разрешены только для функций инструкций. Дополнительные сведения см. в подразделе **выполнение операций инструкции в асинхронном режиме**далее в этой статье.  
  
 ODBC 3,8 в пакете SDK для Windows 7 предлагает асинхронное выполнение операций, связанных с подключением. Дополнительные сведения см. в разделе **выполнение операций подключения асинхронно** далее в этом разделе.  
  
 В пакете SDK для Windows 7 для асинхронных инструкций или операций подключения приложение определило, что асинхронная операция была завершена с помощью метода опроса. Начиная с пакета SDK для Windows 8, можно определить, что асинхронная операция завершена с помощью метода уведомления. Дополнительные сведения см. в разделе [асинхронное выполнение (метод уведомления)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
 По умолчанию драйверы выполняют функции ODBC синхронно; Это значит, что приложение вызывает функцию, и драйвер не возвращает управление приложению до завершения выполнения функции. Однако некоторые функции могут выполняться асинхронно; Это значит, что приложение вызывает функцию, а драйвер после минимальной обработки возвращает управление приложению. Затем приложение может вызвать другие функции, пока первая функция еще выполняется.  
  
 Асинхронное выполнение поддерживается для большинства функций, которые в основном выполняются в источнике данных, таких как функции для установки соединений, подготовки и выполнения инструкций SQL, получения метаданных, извлечения данных и фиксации транзакций. Это наиболее полезно, когда задача, выполняемая в источнике данных, занимает много времени, например процесс входа в систему или сложный запрос к большой базе данных.  
  
 Когда приложение выполняет функцию с инструкцией или соединение, для которого включена асинхронная обработка, драйвер выполняет минимальный объем обработки (например, проверку аргументов ошибок), передает обработку в источник данных и возвращает Управление приложением с помощью SQL_STILL_EXECUTING кода возврата. Затем приложение выполняет другие задачи. Чтобы определить, завершена ли асинхронная функция, приложение опрашивает драйвер через регулярные промежутки времени, вызывая функцию с теми же аргументами, которые использовались изначально. Если функция по-прежнему выполняется, она возвращает SQL_STILL_EXECUTING; Если выполнение завершается, возвращается код, который был бы возвращен в синхронном режиме, например SQL_SUCCESS, SQL_ERROR или SQL_NEED_DATA.  
  
 Будет ли функция выполняться синхронно или асинхронно, зависит от драйвера. Например, предположим, что метаданные результирующего набора кэшируются в драйвере. В этом случае выполнение **SQLDescribeCol** займет очень мало времени, и драйвер должен просто выполнить функцию, а не искусственно отложить выполнение. С другой стороны, если драйверу необходимо получить метаданные из источника данных, он должен вернуть управление приложению во время выполнения этого действия. Поэтому приложение должно иметь возможность обрабатывать код возврата, отличный от SQL_STILL_EXECUTING, когда он сначала выполняет функцию в асинхронном режиме.  
  
## <a name="executing-statement-operations-asynchronously"></a>Асинхронное выполнение операций с инструкциями  
 Следующие функции инструкции работают с источником данных и могут выполняться асинхронно:  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[функция SQLSetPos;](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 Асинхронное выполнение инструкций контролируется либо для каждого из них, либо для каждого отдельного подключения, в зависимости от источника данных. Таким образом, приложение указывает не, что конкретная функция должна выполняться асинхронно, но любая функция, выполняемая в определенной инструкции, должна выполняться асинхронно. Чтобы узнать, какой из поддерживаемых служб, приложение вызывает [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) с возможностью SQL_ASYNC_MODE. SQL_AM_CONNECTION возвращается, если асинхронное выполнение на уровне соединения (для обработчика инструкций) поддерживается; SQL_AM_STATEMENT, если поддерживается асинхронное выполнение на уровне инструкций.  
  
 Чтобы указать, что функции, выполняемые с определенной инструкцией, должны выполняться асинхронно, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_ASYNC_ENABLE и присваивает ему значение SQL_ASYNC_ENABLE_ON. Если асинхронная обработка на уровне соединения поддерживается, атрибут инструкции SQL_ATTR_ASYNC_ENABLE доступен только для чтения и его значение совпадает с атрибутом Connection соединения, для которого была выделена инструкция. Драйвер зависит от того, задано ли значение атрибута инструкции во время выделения инструкции или более поздней версии. При попытке его установки будут возвращены SQL_ERROR и SQLSTATE HYC00 (Необязательная функция не реализована).  
  
 Чтобы указать, что функции, выполняемые с определенным соединением, должны выполняться асинхронно, приложение вызывает **SQLSetConnectAttr** с атрибутом SQL_ATTR_ASYNC_ENABLE и присваивает ему значение SQL_ASYNC_ENABLE_ON. Все последующие дескрипторы инструкций, выделенные для соединения, будут включены для асинхронного выполнения. Он определяется драйвером, независимо от того, будут ли существующие дескрипторы инструкций включены этим действием. Если SQL_ATTR_ASYNC_ENABLE имеет значение SQL_ASYNC_ENABLE_OFF, все инструкции в соединении работают в синхронном режиме. Если асинхронное выполнение включено в связи с активной инструкцией, возвращается ошибка.  
  
 Чтобы определить максимальное количество активных параллельных операторов в асинхронном режиме, которые драйвер может поддерживать для данного соединения, приложение вызывает **SQLGetInfo** с параметром SQL_MAX_ASYNC_CONCURRENT_STATEMENTS.  
  
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
  
 При асинхронном выполнении функции приложение может вызывать функции для любых других инструкций. Приложение также может вызывать функции для любого соединения, за исключением одного, связанного с асинхронной инструкцией. Но приложение может вызвать только исходную функцию и следующие функции (с маркером инструкции или связанным с ним соединением, обработчиком среды) после того, как операция инструкции возвратит SQL_STILL_EXECUTING:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [Склканцелхандле](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (для маркера инструкции)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [Функции SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [Функцию SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Если приложение вызывает любую другую функцию с асинхронной инструкцией или с соединением, связанным с этой инструкцией, функция возвращает значение SQLSTATE HY010 (ошибка последовательности функций), например.  
  
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
  
 Когда приложение вызывает функцию, чтобы определить, выполняется ли оно асинхронно, оно должно использовать исходный маркер инструкции. Это связано с тем, что асинхронное выполнение отсчитывается отдельно для каждого оператора. Приложение также должно предоставить допустимые значения для других аргументов — исходные аргументы позволяют получить прошлую проверку ошибок в диспетчере драйверов. Однако после того, как драйвер проверит обработчик инструкции и определит, что инструкция выполняется асинхронно, она игнорирует все остальные аргументы.  
  
 Хотя функция выполняется асинхронно, то есть после ее возвращения SQL_STILL_EXECUTING и до того, как она возвращает другой код, приложение может отменить его, вызвав **SQLCancel** или **склканцелхандле** с тем же маркером инструкции. Это не гарантирует отмену выполнения функции. Например, функция может уже завершиться. Более того, код, возвращаемый **SQLCancel** или **склканцелхандле** , указывает, была ли попытка отмены функции успешной, а не вне зависимости от того, была ли она отменена. Чтобы определить, была ли отменена функция, приложение снова вызывает функцию. Если функция была отменена, она возвращает SQL_ERROR и SQLSTATE HY008 (операция отменена). Если функция не была отменена, она возвращает другой код, например SQL_SUCCESS, SQL_STILL_EXECUTING или SQL_ERROR с другим SQLSTATE.  
  
 Чтобы отключить асинхронное выполнение определенной инструкции, когда драйвер поддерживает асинхронную обработку на уровне инструкций, приложение вызывает **SQLSetStmtAttr** с атрибутом SQL_ATTR_ASYNC_ENABLE и задает для него значение SQL_ASYNC_ENABLE_OFF. Если драйвер поддерживает асинхронную обработку на уровне соединения, приложение вызывает **SQLSetConnectAttr** , чтобы задать для SQL_ATTR_ASYNC_ENABLE значение SQL_ASYNC_ENABLE_OFF, которое отключает асинхронное выполнение всех инструкций в соединении.  
  
 Приложение должно обрабатывать диагностические записи в повторяющемся цикле исходной функции. Если **SQLGetDiagField** или **SQLGetDiagRec** вызывается при выполнении асинхронной функции, он вернет текущий список записей диагностики. При каждом повторении исходного вызова функции он очищает предыдущие диагностические записи.  
  
## <a name="executing-connection-operations-asynchronously"></a>Асинхронное выполнение операций подключения  
 До ODBC 3,8 асинхронное выполнение было разрешено для операций, связанных с инструкциями, таких как подготовка, выполнение и извлечение, а также для операций с метаданными каталога. Начиная с ODBC 3,8, асинхронное выполнение также возможно для операций, связанных с подключением, таких как подключение, отключение, фиксация и откат.  
  
 Дополнительные сведения об ODBC 3,8 см. [в разделе новые возможности odbc 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
 Асинхронное выполнение операций подключения полезно в следующих сценариях:  
  
-   Если небольшое количество потоков управляет большим количеством устройств с очень высокой скоростью передачи данных. Чтобы повысить скорость реагирования и масштабируемость, желательно, чтобы все операции были асинхронными.  
  
-   Если требуется перекрытие операций базы данных с несколькими соединениями для сокращения времени передачи.  
  
-   Эффективные асинхронные вызовы ODBC и возможность отмены операций подключения позволяют приложению разрешать пользователю отменять любые операции, не дожидаясь истечения времени ожидания.  
  
 Следующие функции, которые работают с дескрипторами подключений, теперь можно выполнять асинхронно:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Чтобы определить, поддерживает ли драйвер асинхронные операции с этими функциями, приложение вызывает **SQLGetInfo** с SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE возвращается, если поддерживаются асинхронные операции. SQL_ASYNC_DBC_NOT_CAPABLE возвращается, если асинхронные операции не поддерживаются.  
  
 Чтобы указать, что функции, выполняемые с определенным соединением, должны выполняться асинхронно, приложение вызывает **SQLSetConnectAttr** и задает атрибуту SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE значение SQL_ASYNC_DBC_ENABLE_ON. Установка атрибута соединения перед установкой соединения всегда выполняется синхронно. Кроме того, операция установки атрибута соединения SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE с **SQLSetConnectAttr** всегда выполняется синхронно.  
  
 Приложение может включить асинхронную операцию перед подключением. Так как диспетчеру драйверов не удается определить, какой драйвер следует использовать перед подключением, диспетчер драйверов всегда будет возвращать значение Success в **SQLSetConnectAttr**. Однако может произойти сбой подключения, если драйвер ODBC не поддерживает асинхронные операции.  
  
 В общем случае может существовать не более одной асинхронной функции, связанной с определенным маркером соединения или обработчиком инструкций. Однако у маркера соединения может быть несколько связанных обработчиков инструкций. Если в обработчике соединения не выполняется асинхронной операции, связанный обработчик инструкции может выполнить асинхронную операцию. Аналогичным образом, если в каком-либо связанном с ним обработчике нет ни одной асинхронной операции, то на его обработку может быть асинхронная операция. Попытка выполнить асинхронную операцию с помощью обработчика, который в данный момент выполняет асинхронную операцию, возвратит HY010, "ошибка последовательности функций".  
  
 Если операция подключения возвращает SQL_STILL_EXECUTING, приложение может вызвать только исходную функцию и следующие функции для этого маркера соединения:  
  
-   **Склканцелхандле** (для маркера подключения)  
  
-   **SQLGetDiagField**  
  
-   **Функции SQLGetDiagRec**  
  
-   **Функцию SQLAllocHandle** (распределение env и DBC)  
  
-   **Склаллочандлестд** (распределение env и DBC)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Приложение должно обрабатывать диагностические записи в повторяющемся цикле исходной функции. Если SQLGetDiagField или SQLGetDiagRec вызывается при выполнении асинхронной функции, он вернет текущий список записей диагностики. При каждом повторении исходного вызова функции он очищает предыдущие диагностические записи.  
  
 Если соединение открывается или закрывается асинхронно, операция завершается, когда приложение получает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO в исходном вызове функции.  
  
 В ODBC 3,8, **склканцелхандле**, добавлена новая функция. Эта функция отменяет шесть функций подключения (**SQLBrowseConnect**, **SQLConnect**, **SQLDisconnect**, **SQLDriverConnect**, **SQLEndTran**и **SQLSetConnectAttr**). Приложение должно вызвать **SQLGetFunctions** , чтобы определить, поддерживает ли драйвер **склканцелхандле**. Как и в случае с **SQLCancel**, если **склканцелхандле** возвращает значение Success, это не означает, что операция была отменена. Приложение должно снова вызвать исходную функцию, чтобы определить, была ли операция отменена. **Склканцелхандле** позволяет отменять асинхронные операции в дескрипторах соединения или дескрипторах инструкций. Использование **склканцелхандле** для отмены операции в маркере инструкции аналогично вызову **SQLCancel**.  
  
 Не требуется одновременно поддерживать операции **склканцелхандле** и асинхронного подключения. Драйвер может поддерживать асинхронные операции подключения, но не **склканцелхандле**, и наоборот.  
  
 Асинхронные операции подключения и **склканцелхандле** также могут использоваться приложениями ODBC 3. x и ODBC 2. x с драйвером ODBC 3,8 и диспетчером драйверов ODBC 3,8. Сведения о том, как включить более старое приложение для использования новых функций в более поздней версии ODBC, см. в разделе [Таблица совместимости](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
### <a name="connection-pooling"></a>Организация пулов соединений  
 При включении пула соединений асинхронные операции будут минимально поддерживаться для установления соединения (с **SQLConnect** и **SQLDriverConnect**) и закрывать соединение с **SQLDisconnect**. Но приложение по-прежнему должно иметь возможность обрабатывать SQL_STILL_EXECUTING возвращаемое значение из **SQLConnect**, **SQLDriverConnect**и **SQLDisconnect**.  
  
 Если включено использование пулов соединений, для асинхронных операций поддерживаются **SQLEndTran** и **SQLSetConnectAttr** .  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Description  
 В следующем примере показано, как использовать **SQLSetConnectAttr** для включения асинхронного выполнения функций, связанных с подключением.  
  
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
  
### <a name="description"></a>Description  
 В этом примере показаны асинхронные операции фиксации. Операции отката также можно выполнить таким образом.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Выполнение инструкций (ODBC)](../../../odbc/reference/develop-app/executing-statements-odbc.md)
