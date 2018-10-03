---
title: Асинхронное выполнение (метод уведомления) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec4b197c6c9588194531c2cc29ee1ba79d51fa6e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669492"
---
# <a name="asynchronous-execution-notification-method"></a>Асинхронное выполнение (метод уведомления)
ODBC позволяет асинхронное выполнение подключения и операций инструкции. Поток приложения можно вызывать функции ODBC в асинхронном режиме, и функция может вернуть, прежде чем операция будет завершена, возвращая поток приложения, для выполнения других задач. В Windows 7 SDK, асинхронные инструкции или операций соединения приложения определить, что асинхронная операция была завершались с использованием метода опроса. Дополнительные сведения см. в разделе [асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Начиная с пакета SDK Windows 8, необходимо выяснить, что асинхронная операция завершена с помощью метода уведомления.  
  
 В методе опроса приложения должны вызвать функцию асинхронной каждый раз, когда ему состояние операции. Метод уведомления аналогична обратного вызова и ожидания в ADO.NET. ODBC, однако использует Win32 события как объект уведомления.  
  
 Библиотека курсоров ODBC и асинхронное уведомление ODBC нельзя использовать одновременно. Установка обоих атрибутов будет сообщение об ошибке с кодом SQLSTATE S1119 (библиотека курсоров и асинхронное уведомление не могут быть включены в то же время).  
  
 См. в разделе [уведомлений асинхронные функции завершения](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) сведения для разработчиков драйверов.  
  
> [!NOTE]  
>  Метод уведомления не поддерживается с библиотекой курсоров. Приложение будет получать сообщение об ошибке при попытке включить библиотеку курсоров через SQLSetConnectAttr, при включении метод уведомления.  
  
## <a name="overview"></a>Обзор  
 При вызове функции ODBC в асинхронном режиме, управление возвращается вызывающему приложению непосредственно с кодом возврата SQL_STILL_EXECUTING. Приложение необходимо многократно выполнять опрос функция, пока не будет возвращено отличен от SQL_STILL_EXECUTING. Цикл опроса увеличение использования ЦП, приводит к снижению производительности во многих сценариях асинхронного.  
  
 Каждый раз, когда используется модель уведомлений, отключен модель опроса. Приложения не должны вызывать исходную функцию еще раз. Вызовите [функция SQLCompleteAsync](../../../odbc/reference/syntax/sqlcompleteasync-function.md) для завершения асинхронной операции. Если приложение вызывает исходную функцию снова до завершения асинхронной операции, вызов вернет значение SQL_ERROR с SQLSTATE IM017 (опроса отключена в асинхронном режиме уведомлений).  
  
 При использовании модели уведомления, приложение может вызвать **SQLCancel** или **SQLCancelHandle** отмены инструкции или соединения. При успешном выполнении запроса отмены ODBC возвращает значение SQL_SUCCESS. Это сообщение указывает, что функция фактически было отменено; он показывает, что запрос на отмену был обработан. — Это ли функция фактически отменяется, зависящих от драйвера и от источника данных. При отмене операции, диспетчер драйверов будут по-прежнему создать событие. Диспетчер драйверов возвращает SQL_ERROR в буфере код возврата и находится в состоянии SQLSTATE HY008 (операция отменена) для указания того, Отмена прошла успешно. Если функция завершения обработки, диспетчер драйверов возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO.  
  
### <a name="downlevel-behavior"></a>Поведение нижнего уровня  
 Версия драйвера ODBC, поддержку этого уведомления на полный — ODBC 3.81.  
  
|Версия приложения ODBC|Версии диспетчера драйверов|Версия драйвера|Поведение|  
|------------------------------|----------------------------|--------------------|--------------|  
|Новое приложение в любой версии ODBC|ODBC 3.81|ODBC 3,80 драйвера|Приложение может использовать эту функцию, если драйвер поддерживает эту функцию, в противном случае диспетчер драйверов завершится ошибкой.|  
|Новое приложение в любой версии ODBC|ODBC 3.81|Драйвер ODBC для пред-3,80|Диспетчер драйверов завершится ошибкой, если драйвер не поддерживает эту функцию.|  
|Новое приложение в любой версии ODBC|Pre-ODBC 3.81|Любой|Когда приложение использует эту функцию, диспетчер старый драйвер будет рассматривать новые атрибуты как специфические для драйвера атрибуты и драйвер должен ошибкой. Новый диспетчер драйверов не передаст эти атрибуты к драйверу.|  
  
 Приложение должно проверить версию диспетчера драйверов перед использованием этой функции. В противном случае если плохо написанного драйвер не ошибка и версии диспетчера драйверов ODBC 3.81 pre, поведение не определено.  
  
## <a name="use-cases"></a>Способы применения  
 В этом разделе показаны варианты использования асинхронного выполнения и механизм опроса.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Интегрировать данные из нескольких источников ODBC  
 Приложение интеграции данных асинхронно извлекает данные из нескольких источников данных. Ниже приведены некоторые данные из удаленных источников данных и являются некоторые данные из локальных файлов. Приложение не может выполняться до завершения асинхронных операций.  
  
 Вместо повторного опрашивания операцию, чтобы определить, если оно завершено, приложение может создавать объект события и свяжите ее с дескриптором соединения ODBC или дескриптор инструкции ODBC. Затем приложение вызывает операционной системы синхронизации API-интерфейсы для ожидания объекта одно событие или многие объекты событий (события ODBC и других событий Windows). ODBC будут сообщать объект события, при завершении соответствующей асинхронной операции ODBC.  
  
 В Windows будет использоваться объекты событий Win32 и, представит пользователю унифицированную модель программирования. Руководители драйвера на других платформах, могут использовать объект реализация событий, определенных для этих платформ.  
  
 В следующем образце кода показано использование подключения и асинхронное уведомление оператора:  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Определение, если драйвер поддерживает асинхронное уведомление  
 Приложение ODBC может определить, поддерживает ли драйвер ODBC асинхронное уведомление, вызвав [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md). Диспетчер драйверов ODBC соответственно вызовет **SQLGetInfo** драйвера с SQL_ASYNC_NOTIFICATION.  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Связывание дескриптор события Win32 с дескриптором ODBC  
 Приложения отвечают за создание объектов событий Win32 с помощью соответствующих функций Win32. Приложение можно связать один дескриптор события Win32 с один дескриптор соединения ODBC или один дескриптор инструкции ODBC.  
  
 Атрибуты соединения SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE и SQL_ATTR_ASYNC_DBC_EVENT определить ли ODBC выполняет в асинхронном режиме и ли ODBC включает режим уведомлений для дескриптора соединения. Атрибуты инструкции атрибуту SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_ASYNC_STMT_EVENT определить ли ODBC выполняет в асинхронном режиме и ли ODBC включает режим уведомлений для дескриптора инструкции.  
  
|Атрибуту SQL_ATTR_ASYNC_ENABLE или SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT или SQL_ATTR_ASYNC_DBC_EVENT|Режим|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Включить|отличное от null|Асинхронное уведомление|  
|Включить|null|Асинхронные опроса|  
|Отключить|any|Синхронная|  
  
 Приложение может временно отключить работы в асинхронном режиме. ODBC не учитывает значения SQL_ATTR_ASYNC_DBC_EVENT при отключении подключения уровня асинхронной операции. ODBC не учитывает значения SQL_ATTR_ASYNC_STMT_EVENT при отключении инструкции уровня асинхронной операции.  
  
 Синхронный вызов из **SQLSetStmtAttr** и **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** поддерживает асинхронные операции, но вызов **SQLSetConnectAttr** присвоить SQL_ATTR_ASYNC_DBC_EVENT всегда выполняется синхронно.  
  
-   **SQLSetStmtAttr** не поддерживает асинхронное выполнение.  
  
 Из-за ошибок сценария  
 Когда **SQLSetConnectAttr** вызывается перед выполнением соединения, диспетчер драйверов не может определить какой драйвер следует использовать. Таким образом, диспетчер драйверов выполнилась успешно для **SQLSetConnectAttr** , но атрибут могут быть не готовы для установки драйвера. Диспетчер драйверов установит эти атрибуты, когда приложение вызывает функцию подключения. Диспетчер драйверов может из-за ошибок, так как драйвер не поддерживает асинхронные операции.  
  
 Наследование из атрибутов соединения  
 Как правило операторы соединения будут наследовать атрибуты соединения. Тем не менее атрибут SQL_ATTR_ASYNC_DBC_EVENT не наследуется и влияет только на операции подключения.  
  
 Чтобы связать обработчик событий с дескриптором соединения ODBC, приложение ODBC вызывает API-Интерфейс ODBC **SQLSetConnectAttr** и указывает SQL_ATTR_ASYNC_DBC_EVENT как атрибут и событие обработки в качестве значения атрибута. Новый атрибут ODBC SQL_ATTR_ASYNC_DBC_EVENT относится к типу SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Как правило приложения создают объекты событий автоматического сброса. ODBC не приведет к сбросу объект события. Приложения необходимо убедиться в том, что объект находится не в сигнальное состояние перед вызовом любой асинхронной функции ODBC.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT является атрибутом только для диспетчера драйверов, который не будет установлен в драйвере.  
  
 Значение по умолчанию SQL_ATTR_ASYNC_DBC_EVENT имеет значение NULL. Если драйвер не поддерживает асинхронное уведомление, получения или задания SQL_ATTR_ASYNC_DBC_EVENT вернет значение SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора).  
  
 Если последнее значение SQL_ATTR_ASYNC_DBC_EVENT на дескриптором соединения ODBC не равно NULL, и приложение включить асинхронный режим, задав для атрибута SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE с SQL_ASYNC_DBC_ENABLE_ON, вызов любого подключения ODBC функция, который поддерживает асинхронный режим получит уведомление о завершении. Если последнее значение SQL_ATTR_ASYNC_DBC_EVENT на дескриптором соединения ODBC имеет значение NULL, ODBC не будет отправлять приложения все уведомления, независимо от того, включен ли асинхронный режим.  
  
 Приложение может задать SQL_ATTR_ASYNC_DBC_EVENT до или после установки атрибута SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Приложения можно установить атрибут SQL_ATTR_ASYNC_DBC_EVENT на дескриптором соединения ODBC до вызова функции подключения (**SQLConnect**, **SQLBrowseConnect**, или  **SQLDriverConnect**). Поскольку диспетчер драйверов ODBC не знает, какой драйвер ODBC, то приложение будет использовать, он возвращает значение SQL_SUCCESS. Когда приложение вызывает функцию подключения, диспетчер драйверов ODBC проверяет, поддерживает ли драйвер асинхронное уведомление. Если драйвер не поддерживает асинхронное уведомление, диспетчер драйверов ODBC возвращает ошибку SQL_ERROR с SQLSTATE S1_118 (драйвер не поддерживает асинхронное уведомление). Если драйвер поддерживает асинхронное уведомление, диспетчер драйверов ODBC вызывает драйвер и задать соответствующие атрибуты SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK и SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 Аналогичным образом, приложение вызывает **SQLSetStmtAttr** при получении инструкции ODBC обработки и задает атрибут SQL_ATTR_ASYNC_STMT_EVENT для включения или отключения асинхронных уведомлений на уровне инструкции. Так как после установления соединения всегда вызывается функция инструкции **SQLSetStmtAttr** вернет значение SQL_ERROR с SQLSTATE S1_118 (драйвер не поддерживает асинхронное уведомление) немедленно в том случае, если соответствующий драйвер не поддерживает асинхронные операции или драйвер поддерживает и асинхронные операции, но не поддерживает асинхронное уведомление.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, который может иметь значение NULL, является атрибутом только для диспетчера драйверов, который не будет установлен в драйвере.  
  
 Значение по умолчанию SQL_ATTR_ASYNC_STMT_EVENT имеет значение NULL. Если драйвер не поддерживает асинхронное уведомление, получения или задания атрибутов SQL_ATTR_ASYNC_ STMT_EVENT вернет значение SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора).  
  
 Приложения не должен связывать одним и тем же дескриптором события с более чем один дескриптор ODBC. В противном случае если два асинхронных вызовов функции ODBC завершается на двух дескрипторов, которые совместно используют этот же дескриптор события одно уведомление будут потеряны. Во избежание дескриптор инструкции, наследования одним и тем же дескриптором события из дескриптора соединения ODBC возвращает SQL_ERROR с SQLSTATE IM016 (невозможно задать атрибут инструкции в дескрипторе соединения), если приложение задает SQL_ATTR_ASYNC_STMT_EVENT на дескриптор соединения.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Вызов функций ODBC, асинхронный  
 После включения асинхронное уведомление и началом асинхронной операции, приложение может вызвать любую функцию ODBC. Если функция принадлежит к набору функций, которые поддерживают асинхронную операцию, приложение будет получать уведомления о завершении после завершения операции, независимо от того, является ли сбой функции или выполнена успешно.  Единственным исключением является то, что приложение вызывает функцию ODBC с недопустимым дескриптором соединения или инструкции. В этом случае ODBC не получить дескриптор события и задать его в сигнальное состояние.  
  
 Приложение должно гарантировать, что объект связанное событие находится в несигнальное состояние перед началом асинхронной операции на соответствующий дескриптор ODBC. ODBC не приведет к сбросу объект события.  
  
### <a name="getting-notification-from-odbc"></a>Получение уведомлений из ODBC  
 Можно вызвать поток приложения **WaitForSingleObject** ожидание дескриптора одного события или вызов **WaitForMultipleObjects** ожидать в массив дескрипторов событий и приостановлена до одного или всех объектов событий сигнальное или по истечении интервала времени ожидания.  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
