---
title: Асинхронное исполнение (Метод опроса) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca7b3d5fa16be44bf4c2ef8f8df8953ae081235d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293404"
---
# <a name="asynchronous-execution-polling-method"></a>Асинхронное выполнение (метод опроса)
До ODBC 3.8 и Windows 7 SDK асинхронные операции допускались только на функции оператора. Для получения дополнительной **Executing Statement Operations Asynchronously**информации, см.  
  
 ODBC 3.8 в Windows 7 SDK ввел асинхронное исполнение операций, связанных с подключением. Для получения дополнительной информации смотрите раздел **«Выполнение операций подключения» асинхронно** раздел, а затем в этой теме.  
  
 В Windows 7 SDK для асинхронных операций оператора или подключения приложение определило, что асинхронная операция была завершена с помощью метода опроса. Начиная с SDK Windows 8, можно определить, что асинхронная операция завершена с помощью метода уведомления. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)  
  
 По умолчанию драйверы выполняют функции ODBC синхронно; то есть приложение вызывает функцию, и драйвер не возвращает управление в приложение до тех пор, пока оно не завершит выполнение функции. Тем не менее, некоторые функции могут быть выполнены асинхронно; то есть приложение вызывает функцию, и драйвер, после минимальной обработки, возвращает управление в приложение. Затем приложение может вызывать другие функции, пока первая функция все еще выполняется.  
  
 Асинхронное выполнение поддерживается для большинства функций, которые в значительной степени выполняются на источнике данных, таких как функции для создания соединений, подготовки и выполнения инструкций По сЗ-Л, получения метаданных, получения данных и транзакций фиксации. Это наиболее полезно, когда выполняемые задачи на источнике данных занимает много времени, например, процесс входа или сложный запрос в отношении большой базы данных.  
  
 Когда приложение выполняет функцию с помощью оператора или соединения, включенного для асинхронной обработки, драйвер выполняет минимальное количество обработки (например, проверка аргументов на наличие ошибок), обработку рук к источнику данных и возврат управления в приложение с SQL_STILL_EXECUTING кодом возврата. Затем приложение выполняет другие задачи. Чтобы определить, когда асинхронная функция закончена, приложение регулярно осваивает драйвер, вызывая функцию с теми же аргументами, что и первоначально. Если функция все еще исполняется, она возвращается SQL_STILL_EXECUTING; если он закончил выполнение, он возвращает код, который он вернул бы, если бы он выполнялся синхронно, например, SQL_SUCCESS, SQL_ERROR или SQL_NEED_DATA.  
  
 Выполняет ли функция синхронно или асинхронно драйвер. Например, предположим, что метаданные набора результатов кэшированы в драйвере. В этом случае выполнение **s'LDescribeCol** занимает очень мало времени, и драйвер должен просто выполнить функцию, а не искусственно задержать выполнение. С другой стороны, если водителю необходимо извлечь метаданные из источника данных, он должен вернуть управление в приложение, пока он делает это. Таким образом, приложение должно быть в состоянии обрабатывать код возврата, кроме SQL_STILL_EXECUTING, когда он впервые выполняет функцию асинхронно.  
  
## <a name="executing-statement-operations-asynchronously"></a>Выполнение операций выписки асинхронно  
 Следующие функции оператора работают на источнике данных и могут выполняться асинхронно:  
  
||||  
|-|-|-|  
|[СЗЛБалКОперации](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[функция SQLSetPos;](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 Асинхронное выполнение оператора контролируется либо по заявлению, либо по основе подключения, в зависимости от источника данных. То есть приложение указывает не на то, что конкретная функция должна выполняться асинхронно, а в том, что любая функция, выполняемый на конкретном заявлении, должна выполняться асинхронно. Чтобы узнать, какой из них поддерживается, приложение вызывает [s'LGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) с опцией SQL_ASYNC_MODE. SQL_AM_CONNECTION возвращается, если поддерживается асинхронное выполнение на уровне соединения (для ручки оператора); SQL_AM_STATEMENT если асинхронное исполнение на уровне оператора поддерживается.  
  
 Чтобы указать, что функции, выполняемые с определенным заявлением, должны выполняться асинхронно, приложение вызывает **S'LSetStmtAttr** с SQL_ATTR_ASYNC_ENABLE атрибутом и устанавливает его на SQL_ASYNC_ENABLE_ON. Если асинхронная обработка уровня соединения поддерживается, атрибут SQL_ATTR_ASYNC_ENABLE оператора читается только и его значение такое же, как атрибут соединения соединения, на котором было выделено заявление. Устанавливается ли значение атрибута оператора во время выделения оператора или позже. Попытка установить его вернет SQL_ERROR и S'LSTATE HYC00 (необязательная функция не реализована).  
  
 Чтобы указать, что функции, выполняемые с определенным соединением, должны выполняться асинхронно, приложение вызывает **S'LSetConnectAttr** с SQL_ATTR_ASYNC_ENABLE атрибутом и устанавливает его на SQL_ASYNC_ENABLE_ON. Все будущие ручки оператора, выделенные на соединение, будут включены для асинхронного выполнения; определяется ли существующими ручками оператора этим действием. Если SQL_ATTR_ASYNC_ENABLE настроена на SQL_ASYNC_ENABLE_OFF, все операторы соединения находятся в синхронном режиме. Ошибка возвращается при включении асинхронного выполнения при наличии активного оператора соединения.  
  
 Чтобы определить максимальное количество активных одновременных инструкций в асинхронном режиме, которое драйвер может поддерживать в данном подключении, приложение вызывает **s'LGetInfo** с SQL_MAX_ASYNC_CONCURRENT_STATEMENTS опцией.  
  
 Следующий код демонстрирует, как работает модель опроса:  
  
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
  
 В то время как функция выполняется асинхронно, приложение может вызывать функции на любых других инструкциях. Приложение также может вызывать функции на любом подключении, за исключением того, что связано с асинхронным заявлением. Но приложение может вызывать только исходную функцию и следующие функции (с ручкой оператора или связанное с ней соединение, ручка среды), после того, как операция оператора возвращается SQL_STILL_EXECUTING:  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [S'LКансканхельстом](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (на ручке оператора)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [Функции SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [СЗЛАллокХэндл](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [СЗЛГетЕнвТтр](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [Источники данных S'LData](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 Если приложение вызывает любую другую функцию с асинхронным заявлением или с подключением, связанным с этим утверждением, функция возвращает, например, S'Lstate HY010 (ошибка последовательности функций.  
  
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
  
 Когда приложение вызывает функцию, чтобы определить, является ли она по-прежнему выполнять асинхронно, он должен использовать исходную ручку оператора. Это происходит потому, что асинхронное исполнение отслеживается на основе в основе в ней. Приложение должно также предоставить действительные значения для других аргументов - первоначальные аргументы будут делать - чтобы получить последние проверки ошибки в драйвер-менеджер. Однако после того, как водитель проверяет ручку оператора и определяет, что заявление исполняется асинхронно, он игнорирует все другие аргументы.  
  
 В то время как функция исполняет асинхронно, т.е. после того, как она вернулась SQL_STILL_EXECUTING и прежде чем она возвращает другой код, приложение может отменить ее, позвонив по **S'LCancel** или **S'LCancelHandle** с той же ручкой оператора. Это не гарантирует отмену выполнения функции. Например, функция может быть уже завершена. Кроме того, код, возвращенный **S'LCancel** или **S'LCancelHandle,** только указывает на то, была ли попытка отменить функцию успешной, а не на самом деле ли она отменила функцию. Чтобы определить, была ли функция отменена, приложение снова вызывает функцию. Если функция была отменена, она возвращает SQL_ERROR и S'Lstate HY008 (Операция отменена). Если функция не была отменена, она возвращает другой код, например, SQL_SUCCESS, SQL_STILL_EXECUTING или SQL_ERROR с другим S'Lstate.  
  
 Чтобы отключить асинхронное выполнение конкретного оператора, когда драйвер поддерживает асинхронную обработку на уровне оператора, приложение вызывает **S'LSetStmtAttr** с SQL_ATTR_ASYNC_ENABLE атрибутом и устанавливает его на SQL_ASYNC_ENABLE_OFF. Если драйвер поддерживает асинхронную обработку на уровне соединения, приложение вызывает **S'LSetConnectAttr,** чтобы установить SQL_ATTR_ASYNC_ENABLE SQL_ASYNC_ENABLE_OFF, что отключает асинхронное выполнение всех инструкций по подключению.  
  
 Приложение должно обрабатывать диагностические записи в повторяющейся петле исходной функции. Если при выполнения асинхронной функции вызывается **s'LGetDiagField** или **S'LGetDiagRec,** он вернет текущий список диагностических записей. Каждый раз, когда исходный вызов функции повторяется, он очищает предыдущие диагностические записи.  
  
## <a name="executing-connection-operations-asynchronously"></a>Выполнение операций подключения асинхронно  
 До ODBC 3.8 асинхронное выполнение было разрешено для операций, связанных с выписками, таких как подготовка, выполнение и извлечение, а также для операций метаданных каталога. Начиная с ODBC 3.8, асинхонное выполнение также возможно для операций, связанных с подключением, таких как подключение, отключение, коммит и откат.  
  
 Для получения дополнительной информации о ODBC 3.8, [см.](../../../odbc/reference/what-s-new-in-odbc-3-8.md)  
  
 Выполнение операций соединения асинхронно полезно в следующих сценариях:  
  
-   Когда небольшое количество потоков управляет большим количеством устройств с очень высокой скоростью передачи данных. Для максимальной отзывчивости и масштабируемости желательно, чтобы все операции были асинхронными.  
  
-   При перекрытии операций базы данных по нескольким соединениям, чтобы сократить время передачи.  
  
-   Эффективные асинхронные вызовы ODBC и возможность отмены операций соединения позволяют пользователю отменять любую медленную операцию без необходимости ждать тайм-аутов.  
  
 Следующие функции, которые работают на ручках соединения, теперь могут выполняться асинхронно:  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[СЗЛДИСКоннект](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 Чтобы определить, поддерживает ли драйвер асинхронные операции на этих функциях, приложение вызывает **s'LGetInfo** с SQL_ASYNC_DBC_FUNCTIONS. SQL_ASYNC_DBC_CAPABLE возвращается при поддержке асинхронных операций. SQL_ASYNC_DBC_NOT_CAPABLE возвращается, если асинхронные операции не поддерживаются.  
  
 Чтобы указать, что функции, выполняемые с определенным соединением, должны выполняться асинхронно, приложение вызывает **S'LSetConnectAttr** и устанавливает SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE атрибут SQL_ASYNC_DBC_ENABLE_ON. Установка атрибута соединения перед созданием соединения всегда выполняется синхронно. Кроме того, операция, устанавливая атрибут соединения SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE с **S'LSetConnectAttr,** всегда выполняется синхронно.  
  
 Приложение может включить асинхронную операцию перед подключением. Поскольку менеджер драйвера не может определить, какой драйвер использовать перед подключением, менеджер драйвера всегда будет возвращать успех в **S'LSetConnectAttr.** Однако он может не подключиться, если драйвер ODBC не поддерживает асинхронные операции.  
  
 Как правило, может быть не более одной асинхронно исполняемых функций, связанных с определенной ручкой соединения или ручкой оператора. Однако ручка соединения может иметь несколько связанных с ней рукояток оператора. Если на рукоятке соединения нет асинхронной операции, ассоциированная ручка оператора может выполнять асинхронную операцию. Аналогичным образом, на рукоятке соединения может быть асинхронная операция, если на любой связанной ручке оператора не ведется асинхронных операций. Попытка выполнения асинхронной операции с помощью ручки, выполняющей в настоящее время асинхронную операцию, вернет HY010, "Ошибка последовательности функций".  
  
 Если операция подключения возвращается SQL_STILL_EXECUTING, приложение может вызвать только исходную функцию и следующие функции для этой ручки соединения:  
  
-   **S'LКансканхельстом** (на ручке соединения)  
  
-   **SQLGetDiagField**  
  
-   **Функции SQLGetDiagRec**  
  
-   **СЗЛАллокхельс** (выделение ENV/DBC)  
  
-   **СЗЛАлокХейлст** (выделение ENV/DBC)  
  
-   **СЗЛГетЕнвТтр**  
  
-   **SQLGetConnectAttr**  
  
-   **Источники данных S'LData**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 Приложение должно обрабатывать диагностические записи в повторяющейся петле исходной функции. Если при выполнения асинхронной функции вызывается s'LGetDiagField или S'LGetDiagRec, он вернет текущий список диагностических записей. Каждый раз, когда исходный вызов функции повторяется, он очищает предыдущие диагностические записи.  
  
 Если соединение открывается или закрывается асинхронно, операция завершается, когда приложение получает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO в исходном вызове функции.  
  
 Новая функция была добавлена к ODBC 3.8, **S'LКансканхальд**. Эта функция отменяет шесть функций подключения **(S'LBrowseConnect**, **S'LConnect**, **S'LDisconnect**, **S'LDriverConnect**, **S'LEndTran**, и **S'LSetConnectAttr**). Приложение должно вызвать **S'LGetFunctions,** чтобы определить, поддерживает ли драйвер **S'LКансмотив.** Как и в случае с **S'LCancel**, если **S'LCancelHandle** возвращает успех, это не означает, что операция была отменена. Приложение должно снова вызвать исходную функцию, чтобы определить, была ли отменена операция. **SLCancelHandle** позволяет отменить асинхронные операции на ручках соединения или ручках оператора. Использование **sLCancelHandle** для отмены операции на ручке оператора равномнее вызову **S'LCancel.**  
  
 Не требуется одновременно поддерживать операции по асинхронной связи и асинхронное соединение. **SQLCancelHandle** Водитель может поддерживать асинхронные операции соединения, но не **S'LКансортикрев,** или наоборот.  
  
 Асинхронные операции соединения и **S'LКансканхенд** также могут быть использованы приложениями ODBC 3.x и ODBC 2.x с драйвером ODBC 3.8 и менеджером драйвера ODBC 3.8. Для получения информации о том, как включить старое приложение для использования новых функций в более поздней версии ODBC, [см.](../../../odbc/reference/develop-app/compatibility-matrix.md)  
  
### <a name="connection-pooling"></a>Объединение подключений в пул  
 Всякий раз, когда объединение соединения включено, асинхронные операции поддерживаются лишь минимально для установления соединения (с **S'LConnect** и **S'LDriverConnect)** и закрытия соединения с **S'LDisconnect.** Но приложение все равно должно быть в состоянии обрабатывать SQL_STILL_EXECUTING значение возврата от **S'LConnect**, **S'LDriverConnect**, и **S'LDisconnect**.  
  
 При включении объединения соединений для асинхронных операций поддерживается **поддержка s'LEndTran** и **S'LSetConnectAttr.**  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показано, как использовать **S'LSetConnectAttr** для обеспечения асинхронного выполнения функций, связанных с подключением.  
  
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
 Этот пример показывает асинхронные операции фиксации. Операции отката также могут быть сделаны таким образом.  
  
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
 [Выполнение заявлений ODBC](../../../odbc/reference/develop-app/executing-statements-odbc.md)
