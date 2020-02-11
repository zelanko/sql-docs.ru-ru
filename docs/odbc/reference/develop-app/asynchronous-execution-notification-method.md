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
ms.openlocfilehash: 66b806b698164b306eee4dc7d4c48fbe7835adae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077066"
---
# <a name="asynchronous-execution-notification-method"></a>Асинхронное выполнение (метод уведомления)
ODBC обеспечивает асинхронное выполнение операций подключения и инструкций. Поток приложения может вызывать функцию ODBC в асинхронном режиме, а функция может возвращать до завершения операции, позволяя потоку приложения выполнять другие задачи. В пакете SDK для Windows 7 для асинхронных инструкций или операций подключения приложение определило, что асинхронная операция была завершена с помощью метода опроса. Дополнительные сведения см. в разделе [асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Начиная с пакета SDK для Windows 8, можно определить, что асинхронная операция завершена с помощью метода уведомления.  
  
 В методе опроса приложениям необходимо вызывать асинхронную функцию каждый раз, когда ей требуется состояние операции. Метод уведомления аналогичен обратному вызову и ожидает в ADO.NET. Однако ODBC использует события Win32 в качестве объекта уведомления.  
  
 Библиотеку курсоров ODBC и асинхронное уведомление ODBC нельзя использовать одновременно. Если задать оба атрибута, будет возвращена ошибка с SQLSTATE S1119 (невозможно одновременно включить библиотеку курсоров и асинхронное уведомление).  
  
 Сведения для разработчиков драйверов см. в разделе [уведомление о завершении асинхронной функции](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) .  
  
> [!NOTE]  
>  Метод уведомления не поддерживается в библиотеке курсоров. Приложение получит сообщение об ошибке, если оно попытается включить библиотеку курсоров через SQLSetConnectAttr, если включен метод уведомления.  
  
## <a name="overview"></a>Обзор  
 При вызове функции ODBC в асинхронном режиме элемент управления возвращается вызывающему приложению немедленно с кодом возврата SQL_STILL_EXECUTING. Приложение должно периодически опрашивать функцию, пока не вернет что-либо, кроме SQL_STILL_EXECUTING. Цикл опроса увеличивает загрузку ЦП, что приводит к снижению производительности во многих асинхронных сценариях.  
  
 При использовании модели уведомления модель опроса отключается. Приложения не должны повторно вызывать исходную функцию. Вызовите [функцию склкомплетеасинк](../../../odbc/reference/syntax/sqlcompleteasync-function.md) для завершения асинхронной операции. Если приложение вызывает исходную функцию снова до завершения асинхронной операции, вызов возвратит SQL_ERROR с параметром SQLSTATE IM017 (опрос отключен в режиме асинхронного уведомления).  
  
 При использовании модели уведомления приложение может вызвать **SQLCancel** или **склканцелхандле** для отмены инструкции или операции подключения. Если запрос на отмену выполнен успешно, ODBC возвратит SQL_SUCCESS. Это сообщение не указывает на фактическую отмену функции. Указывает, что запрос отмены обработан. Фактическая отмена функции зависит от драйвера, а также от источника данных. При отмене операции диспетчер драйверов по-прежнему будет сообщать о событии. Диспетчер драйверов возвращает SQL_ERROR в буфере кода возврата, а состояние — SQLSTATE HY008 (операция отменена), чтобы указать, что отмена выполнена успешно. Если функция завершила нормальную обработку, диспетчер драйверов возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO.  
  
### <a name="downlevel-behavior"></a>Поведение нижнего уровня  
 Версия диспетчера драйверов ODBC, поддерживающая это уведомление, по завершении — это ODBC 3,81.  
  
|Версия ODBC приложения|Версия диспетчера драйверов|Версия драйвера|Поведение|  
|------------------------------|----------------------------|--------------------|--------------|  
|Новое приложение любой версии ODBC|ODBC 3,81|Драйвер ODBC 3,80|Приложение может использовать эту функцию, если драйвер поддерживает эту функцию, в противном случае произойдет ошибка диспетчера драйверов.|  
|Новое приложение любой версии ODBC|ODBC 3,81|Драйвер пред-ODBC 3,80|Если драйвер не поддерживает эту функцию, диспетчер драйверов выдаст ошибку.|  
|Новое приложение любой версии ODBC|Пред-ODBC 3,81|Любой|Когда приложение использует эту функцию, старый диспетчер драйверов будет рассматривать новые атрибуты как атрибуты, относящиеся к драйверу, и драйверу следует выпустить ошибку. Новый диспетчер драйверов не будет передавать эти атрибуты драйверу.|  
  
 Перед использованием этой функции приложение должно проверить версию диспетчера драйверов. В противном случае, если плохо написанный драйвер не выдает ошибку и версия диспетчера драйверов до ODBC 3,81, поведение не определено.  
  
## <a name="use-cases"></a>Варианты использования  
 В этом разделе показаны варианты использования асинхронного выполнения и механизма опроса.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Интеграция данных из нескольких источников ODBC  
 Приложение интеграции данных асинхронно извлекает данные из нескольких источников данных. Некоторые данные относятся к удаленным источникам данных, а некоторые — из локальных файлов. Приложение не может продолжать работу до завершения асинхронных операций.  
  
 Вместо многократного опроса операции для определения ее полноты приложение может создать объект события и связать его с обработчиком соединения ODBC или с обработчиком инструкций ODBC. Затем приложение вызывает API синхронизации операционной системы для ожидания одного объекта события или нескольких объектов событий (как событий ODBC, так и других событий Windows). ODBC будет сообщать об объекте события при завершении соответствующей асинхронной операции ODBC.  
  
 В Windows будут использоваться объекты событий Win32, которые будут предоставлять пользователю унифицированную модель программирования. Диспетчеры драйверов на других платформах могут использовать реализацию объектов событий, относящуюся к этим платформам.  
  
 В следующем примере кода показано использование асинхронного уведомления о соединении и инструкции.  
  
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
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Определение того, поддерживает ли драйвер Асинхронное уведомление  
 Приложение ODBC может определить, поддерживает ли драйвер ODBC Асинхронное уведомление путем вызова [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md). Следовательно, диспетчер драйверов ODBC будет вызывать **SQLGetInfo** драйвера с SQL_ASYNC_NOTIFICATION.  
  
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
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Связывание обработчика событий Win32 с помощью обработчика ODBC  
 Приложения отвечают за создание объектов событий Win32 с помощью соответствующих функций Win32. Приложение может связать один обработчик событий Win32 с одним обработчиком соединения ODBC или с одним обработчиком инструкций ODBC.  
  
 Атрибуты соединения SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE и SQL_ATTR_ASYNC_DBC_EVENT определяют, будет ли ODBC выполняться в асинхронном режиме и будет ли ODBC использовать режим уведомления для обработчика соединения. Атрибуты инструкции SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_ASYNC_STMT_EVENT определяют, будет ли ODBC выполняться в асинхронном режиме и будет ли ODBC включать режим уведомления для обработчика инструкций.  
  
|SQL_ATTR_ASYNC_ENABLE или SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT или SQL_ATTR_ASYNC_DBC_EVENT|Режим|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Включить|не равно null|Асинхронное уведомление|  
|Включить|null|Асинхронный опрос|  
|Отключить|любой|Синхронный|  
  
 Приложение может временно отключить асинхронный режим работы. ODBC игнорирует значения SQL_ATTR_ASYNC_DBC_EVENT, если асинхронная операция уровня соединения отключена. ODBC игнорирует значения SQL_ATTR_ASYNC_STMT_EVENT, если асинхронная операция уровня инструкции отключена.  
  
 Синхронный вызов **SQLSetStmtAttr** и **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** поддерживает асинхронные операции, но вызов **SQLSetConnectAttr** для установки SQL_ATTR_ASYNC_DBC_EVENT всегда является синхронным.  
  
-   **SQLSetStmtAttr** не поддерживает асинхронное выполнение.  
  
 Сценарий исходящей ошибки  
 При вызове **SQLSetConnectAttr** перед подключением диспетчер драйверов не сможет определить, какой драйвер следует использовать. Таким образом, диспетчер драйверов возвращает значение Success для **SQLSetConnectAttr** , но атрибут может быть не готов к установке в драйвере. Диспетчер драйверов установит эти атрибуты, когда приложение вызовет функцию подключения. Диспетчер драйверов может выходить из-за ошибки, так как драйвер не поддерживает асинхронные операции.  
  
 Наследование атрибутов соединения  
 Как правило, инструкции соединения наследуют атрибуты соединения. Однако атрибут SQL_ATTR_ASYNC_DBC_EVENT не наследуется и влияет только на операции подключения.  
  
 Чтобы связать обработчик событий с обработчиком соединения ODBC, приложение ODBC вызывает API ODBC **SQLSetConnectAttr** и указывает SQL_ATTR_ASYNC_DBC_EVENT в качестве атрибута и обработчика события в качестве значения атрибута. Новый атрибут ODBC SQL_ATTR_ASYNC_DBC_EVENT имеет тип SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Обычно приложения создают объекты событий автоматического сброса. ODBC не будет сбрасывать объект события. Перед вызовом любой асинхронной функции ODBC приложения должны убедиться, что объект не находится в сигнальном состоянии.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT — это атрибут только для диспетчера драйверов, который не будет установлен в драйвере.  
  
 Значение по умолчанию SQL_ATTR_ASYNC_DBC_EVENT равно NULL. Если драйвер не поддерживает асинхронное уведомление, то при получении или установке SQL_ATTR_ASYNC_DBC_EVENT будет возвращено SQL_ERROR с HY092 SQLSTATE (недопустимый идентификатор атрибута или параметра).  
  
 Если Последнее значение SQL_ATTR_ASYNC_DBC_EVENT, заданное для обработчика соединений ODBC, не равно NULL и асинхронный режим приложения, поддерживающий приложение, установка атрибута SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE с SQL_ASYNC_DBC_ENABLE_ON, вызов любого подключения ODBC функция, которая поддерживает асинхронный режим, получит уведомление о завершении. Если Последнее значение SQL_ATTR_ASYNC_DBC_EVENT, установленное для обработчика соединений ODBC, имеет значение NULL, ODBC не будет передавать приложение ни одного уведомления, независимо от того, включен ли асинхронный режим.  
  
 Приложение может задать SQL_ATTR_ASYNC_DBC_EVENT до или после установки атрибута SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Приложения могут установить атрибут SQL_ATTR_ASYNC_DBC_EVENT для обработчика соединения ODBC перед вызовом функции подключения (**SQLConnect**, **SQLBrowseConnect**или **SQLDriverConnect**). Поскольку диспетчер драйверов ODBC не знает, какой драйвер ODBC будет использоваться приложением, он возвратит SQL_SUCCESS. Когда приложение вызывает функцию подключения, диспетчер драйверов ODBC будет проверять, поддерживает ли драйвер Асинхронное уведомление. Если драйвер не поддерживает асинхронное уведомление, диспетчер драйверов ODBC возвратит SQL_ERROR с S1_118 SQLSTATE (драйвер не поддерживает асинхронное уведомление). Если драйвер поддерживает асинхронное уведомление, диспетчер драйверов ODBC вызывает драйвер и устанавливает соответствующие атрибуты SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK и SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 Аналогичным образом приложение вызывает **SQLSetStmtAttr** в обработчике инструкций ODBC и указывает атрибут SQL_ATTR_ASYNC_STMT_EVENT, чтобы включить или отключить Асинхронное уведомление об уровне инструкций. Поскольку функция оператора всегда вызывается после установления соединения, **SQLSetStmtAttr** возвращает SQL_ERROR с S1_118 SQLSTATE (драйвер не поддерживает асинхронное уведомление) немедленно, если соответствующий драйвер не поддерживает асинхронные операции или драйвер поддерживает асинхронные операции, но не поддерживает асинхронные уведомления.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, для которого можно задать значение NULL, является атрибутом только для диспетчера драйверов, который не будет установлен в драйвере.  
  
 Значение по умолчанию SQL_ATTR_ASYNC_STMT_EVENT равно NULL. Если драйвер не поддерживает асинхронное уведомление, получение или задание SQL_ATTR_ASYNC_ STMT_EVENT атрибут будет возвращать SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра).  
  
 Приложение не должно связывать один и тот же обработчик событий с несколькими обработчиками ODBC. В противном случае одно уведомление будет потеряно, если два асинхронных вызова функции ODBC завершены для двух дескрипторов, использующих один и тот же дескриптор события. Чтобы не наследовать маркеру события, наследующему от обработчика соединения, ODBC возвращает SQL_ERROR с параметром SQLSTATE IM016 (не может установить атрибут инструкции в обработчике соединения), если приложение устанавливает SQL_ATTR_ASYNC_STMT_EVENT в обработчике соединения.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Вызов асинхронных функций ODBC  
 После включения асинхронного уведомления и запуска асинхронной операции приложение может вызвать любую функцию ODBC. Если функция принадлежит к набору функций, поддерживающих асинхронную операцию, приложение получит уведомление о завершении выполнения операции, независимо от того, завершилась ли функция ошибкой или нет.  Единственным исключением является то, что приложение вызывает функцию ODBC с недопустимым соединением или обработчиком инструкции. В этом случае ODBC не будет получать дескриптор события и присвоить ему сигнальное состояние.  
  
 Приложение должно убедиться, что связанный объект события находится в несигнальном состоянии, прежде чем запускать асинхронную операцию с соответствующим дескриптором ODBC. ODBC не будет сбрасывать объект события.  
  
### <a name="getting-notification-from-odbc"></a>Получение уведомлений из ODBC  
 Поток приложения может вызывать **WaitForSingleObject** для ожидания одного дескриптора события или вызова **WaitForMultipleObjects** для ожидания массива дескрипторов событий и приостанавливаться до тех пор, пока один или все объекты событий не станут сигнальными или не истечет интервал времени ожидания.  
  
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
