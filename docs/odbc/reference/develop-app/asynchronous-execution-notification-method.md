---
title: Асинхронное исполнение (метод уведомления) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 250e71dcb47d44a6e437d12c269ea23fa6fb3c2c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306415"
---
# <a name="asynchronous-execution-notification-method"></a>Асинхронное выполнение (метод уведомления)
ODBC позволяет асинхронно выполнять операции соединения и оператора. Поток приложения может вызывать функцию ODBC в асинхронном режиме, а функция может вернуться до завершения операции, что позволяет потоку приложения выполнять другие задачи. В Windows 7 SDK для асинхронных операций оператора или подключения приложение определило, что асинхронная операция была завершена с помощью метода опроса. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md) Начиная с SDK Windows 8, можно определить, что асинхронная операция завершена с помощью метода уведомления.  
  
 В методе опроса приложениядолжны вызывать асинхронную функцию каждый раз, когда она хочет статус операции. Метод уведомления аналогичен обратным вызовам и ожиданию в ADO.NET. ОДНАКо ODBC использует события Win32 в качестве объекта уведомлений.  
  
 Библиотека ODBC Cursor и асинхронное уведомление ODBC не могут использоваться одновременно. Установка обоих атрибутов вернет ошибку с помощью S'LSTATE S1119 (Библиотека Cursor и асинхронное уведомление не могут быть включены одновременно).  
  
 Для получения информации для разработчиков драйверов смотрите [уведомление об асинхронном завершении функций.](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md)  
  
> [!NOTE]  
>  Метод уведомления не поддерживается библиотекой курсоров. Приложение будет получать сообщение об ошибке, если оно попытается включить библиотеку курсоров через S'LSetConnectAttr, когда будет включен метод уведомления.  
  
## <a name="overview"></a>Обзор  
 При вызове функции ODBC в асинхронном режиме элемент управления немедленно возвращается в вызываемый приложение с кодом возврата SQL_STILL_EXECUTING. Приложение должно повторно опросить функцию, пока она не возвращает что-то другое, чем SQL_STILL_EXECUTING. Цикл опроса увеличивает использование процессора, вызывая низкую производительность во многих асинхронных сценариях.  
  
 Всякий раз, когда используется модель уведомления, модель опроса отключается. Приложения не должны снова вызывать исходную функцию. Вызов [функции S'LCompleteAsync](../../../odbc/reference/syntax/sqlcompleteasync-function.md) для завершения асинхронной операции. Если приложение снова вызывает исходную функцию до завершения асинхронной операции, вызов возвращается SQL_ERROR с помощью S'LSTATE IM017 (Опрос отключен в асинхронном режиме уведомления).  
  
 При использовании модели уведомлений приложение может вызвать **S'LCancel** или **S'LКансорт,** чтобы отменить выписку или операцию подключения. Если запрос на отмену будет успешным, ODBC вернется SQL_SUCCESS. Это сообщение не указывает на то, что функция была фактически отменена; он указывает, что запрос на отмену был обработан. Действительно ли функция отменена, зависит от драйвера и зависит от источников данных. При отмене операции менеджер драйвера по-прежнему сигнализирует о событии. Менеджер драйвера возвращает SQL_ERROR в буфере обратного кода, а состояние s'Lstate HY008 (Операция отменена), чтобы указать, что отмена прошла успешно. Если функция завершила нормальную обработку, менеджер драйвера возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO.  
  
### <a name="downlevel-behavior"></a>Поведение на низхи  
 Версия менеджера драйверов ODBC, поддерживающая это уведомление, — ODBC 3.81.  
  
|Версия приложения ODBC|Версия менеджера драйвера|Версия драйвера|Поведение|  
|------------------------------|----------------------------|--------------------|--------------|  
|Новое применение любой версии ODBC|ODBC 3.81|Водитель ODBC 3.80|Приложение может использовать эту функцию, если драйвер поддерживает эту функцию, в противном случае менеджер драйвера будет ошибки.|  
|Новое применение любой версии ODBC|ODBC 3.81|Предварительно ODBC 3.80 Водитель|Менеджер драйвера будет исправиться, если драйвер не поддерживает эту функцию.|  
|Новое применение любой версии ODBC|Предварительно ODBC 3.81|Любой|Когда приложение использует эту функцию, старый менеджер драйвера будет рассматривать новые атрибуты как атрибуты, связанные с драйвером, и драйвер должен ошибиться. Новый менеджер драйвера не будет передавать эти атрибуты водителю.|  
  
 Перед использованием этой функции приложение должно проверить версию менеджера драйверов. В противном случае, если плохо написанный драйвер не ошибается, а версия Driver Manager предварительно ODBC 3.81, поведение не определено.  
  
## <a name="use-cases"></a>Варианты использования  
 В этом разделе показаны случаи использования для асинхронного исполнения и механизм опроса.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Интеграция данных из нескольких источников ODBC  
 Приложение интеграции данных асинхронно получает данные из нескольких источников данных. Некоторые данные получены из удаленных источников данных, а некоторые данные взяты из локальных файлов. Приложение не может продолжаться до тех пор, пока асинхронные операции не будут завершены.  
  
 Вместо того, чтобы повторно опрашивать операцию, чтобы определить, завершена ли она, приложение может создать объект события и связать его с ручкой соединения ODBC или ручкой оператора ODBC. Затем приложение вызывает аБО синхронизации операционной системы для ожидания на одном объекте события или многих объектах событий (как события ODBC, так и другие события Windows). ODBC будет сигнализировать объект события, когда соответствующая асинхронная операция ODBC будет завершена.  
  
 На Windows будут использоваться объекты событий Win32, которые обеспечат пользователю единую модель программирования. Менеджеры драйверов на других платформах могут использовать реализацию объекта события, специфичная для этих платформ.  
  
 Следующий пример кода демонстрирует использование асинхронного уведомления о подключении и выписке:  
  
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
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Определение того, поддерживает ли драйвер асинхронное уведомление  
 Приложение ODBC может определить, поддерживает ли драйвер ODBC асинхронное уведомление, позвонив по [телефону S'LGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md) Менеджер драйвера ODBC, следовательно, вызовет **S'LGetInfo** водителя с SQL_ASYNC_NOTIFICATION.  
  
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
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Связывание ручки событий Win32 с ручкой ODBC  
 Приложения отвечают за создание объектов событий Win32 с использованием соответствующих функций Win32. Приложение может связать одну ручку событий Win32 с одной ручкой соединения ODBC или одной ручкой оператора оператора ODBC.  
  
 Атрибуты соединения SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE и SQL_ATTR_ASYNC_DBC_EVENT определяют, выполняет ли ODBC в асинхронном режиме и позволяет ли ODBC использовать режим уведомления для ручки соединения. Атрибуты оператора SQL_ATTR_ASYNC_ENABLE и SQL_ATTR_ASYNC_STMT_EVENT определяют, выполняет сяочве в асинхронном режиме и позволяет ли ODBC использовать режим уведомления для ручки оператора.  
  
|SQL_ATTR_ASYNC_ENABLE или SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT или SQL_ATTR_ASYNC_DBC_EVENT|Режим|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Включить|ненулевые|Асинхронное уведомление|  
|Включить|null|Асинхронный опрос|  
|Отключить|any|Синхронная|  
  
 Приложение может временно отключить асинхронный режим работы. ODBC игнорирует значения SQL_ATTR_ASYNC_DBC_EVENT если асинхронная операция уровня соединения отключена. ODBC игнорирует значения SQL_ATTR_ASYNC_STMT_EVENT если асинхронная операция уровня оператора отключена.  
  
 Синхронный вызов **S'LSetStmtAttr** и **S'LSetConnectAttr**  
 -   **SLSetConnectAttr** поддерживает асинхронные операции, но вызов **S'LSetConnectAttr** для установки SQL_ATTR_ASYNC_DBC_EVENT всегда синхронный.  
  
-   **SLSetStmtAttr** не поддерживает асинхронное исполнение.  
  
 Сценарий ошибки  
 Когда перед подключением вызывается **sLSetConnectAttr,** менеджер драйвера не может определить, какой драйвер использовать. Таким образом, менеджер драйвера возвращает успех для **S'LSetConnectAttr,** но атрибут может быть не готов к установке в драйвере. Менеджер драйвера установит эти атрибуты, когда приложение вызывает функцию соединения. Менеджер драйвера может выйти из-под действия, поскольку драйвер не поддерживает асинхронные операции.  
  
 Наследование атрибутов соединения  
 Как правило, операторы соединения наследуют атрибуты соединения. Однако атрибут SQL_ATTR_ASYNC_DBC_EVENT не наследуется и влияет только на операции соединения.  
  
 Чтобы связать ручку события с ручкой соединения ODBC, приложение ODBC вызывает ODBC API **S'LSetConnectAttr** и определяет SQL_ATTR_ASYNC_DBC_EVENT как атрибут и ручку события как значение атрибута. Новый атрибут ODBC SQL_ATTR_ASYNC_DBC_EVENT имеет тип SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Обычно приложения создают объекты событий автоматической перезагрузки. ODBC не будет сбросить объект события. Приложения должны убедиться, что объект не находится в сигнальном состоянии, прежде чем вызывать любую асинхронную функцию ODBC.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT является атрибутом только для диспетчера драйверов, который не будет установлен в драйвере.  
  
 Значение SQL_ATTR_ASYNC_DBC_EVENT по умолчанию является NULL. Если драйвер не поддерживает асинхронное уведомление, получение или установка SQL_ATTR_ASYNC_DBC_EVENT вернется SQL_ERROR с помощью S'LSTATE HY092 (идентификатор атрибута/опциона).  
  
 Если последнее SQL_ATTR_ASYNC_DBC_EVENT значение, установленное на ручке соединения ODBC, не является НУДИ, а приложение включило асинхронный режим, установив атрибут SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE с SQL_ASYNC_DBC_ENABLE_ON, вызов любой функции соединения ODBC, поддерживающей асинхронный режим, получит уведомление о завершении. Если последнее SQL_ATTR_ASYNC_DBC_EVENT значение, установленное на ручке соединения ODBC, является NULL, ODBC не будет отправлять приложению никаких уведомлений, независимо от того, включен ли асинхронный режим.  
  
 Приложение может установить SQL_ATTR_ASYNC_DBC_EVENT до или после установки атрибута SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Приложения могут установить атрибут SQL_ATTR_ASYNC_DBC_EVENT на ручке соединения ODBC, прежде чем вызывать функцию подключения **(S'LConnect,** **S'LBrowseConnect,** или **S'LDriverConnect).** Поскольку менеджер драйвера ODBC не знает, какой драйвер ODBC будет использовать приложение, он вернется SQL_SUCCESS. Когда приложение вызывает функцию соединения, менеджер драйвера ODBC проверяет, поддерживает ли драйвер асинхронное уведомление. Если драйвер не поддерживает асинхронное уведомление, менеджер драйвера ODBC вернется SQL_ERROR с S1_118 S'Lstate (Driver не поддерживает асинхронное уведомление). Если драйвер поддерживает асинхронное уведомление, менеджер драйвера ODBC позвонит водителю и установит соответствующие атрибуты SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK и SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 Аналогичным образом, приложение вызывает **S'LSetStmtAttr** на ручке оператора ODBC и определяет SQL_ATTR_ASYNC_STMT_EVENT атрибут, чтобы включить или отключить асинхронное уведомление уровня оператора. Поскольку функция оператора всегда вызывается после установки соединения, **S'LSetStmtAttr** возвращается SQL_ERROR с S1_118 S'Lstate (Driver не поддерживает асинхронное уведомление) сразу же, если соответствующий драйвер не поддерживает асинхронные операции или водитель поддерживает асинхронную работу, но не поддерживает асинхронное уведомление.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, который может быть установлен на NULL, является атрибутом только для менеджера драйвера, который не будет установлен в драйвере.  
  
 Значение SQL_ATTR_ASYNC_STMT_EVENT по умолчанию является NULL. Если драйвер не поддерживает асинхронное уведомление, получение или настройка SQL_ATTR_ASYNC_ STMT_EVENT атрибута вернется SQL_ERROR с помощью s'LSTATE HY092 (идентификатор атрибута/опциона Invalid).  
  
 Приложение не должно связывать одну и ту же ручку событий с более чем одной ручкой ODBC. В противном случае одно уведомление будет потеряно, если два асинхронных вызова функции ODBC будут выполнены на двух ручках, которые разделяют одну и ту же рукоятки событий. Чтобы избежать ручки оператора, нанаследованной той же ручкой события от ручки соединения, ODBC возвращает SQL_ERROR с s'Lstate IM016 (не удается заложить атрибут оператора в ручку соединения), если приложение устанавливает SQL_ATTR_ASYNC_STMT_EVENT на ручку соединения.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Вызов асинхронных функций ODBC  
 После включения асинхронного уведомления и запуска асинхронной операции приложение может вызвать любую функцию ODBC. Если функция относится к набору функций, поддерживающих асинхронную операцию, приложение получит уведомление о завершении операции, независимо от того, была ли функция выполнена или успешно завершена.  Единственным исключением является то, что приложение вызывает функцию ODBC с недействительной ручкой соединения или оператора. В этом случае ODBC не получит ручку события и не установит ее в состояние сигнала.  
  
 Приложение должно убедиться, что связанный объект события находится в несигнальном состоянии перед запуском асинхронной операции на соответствующей ручке ODBC. ODBC не будет сбросить объект события.  
  
### <a name="getting-notification-from-odbc"></a>Получение уведомления от ODBC  
 Поток приложения может вызвать **WaitForSingleObject,** чтобы подождать на одной ручке события или вызвать **WaitForMultipleObjects,** чтобы подождать на массиве декретов событий и быть приостановленным до тех пор, пока один или все объекты события не станут сигнализировать или интервал тайм-аута не пройдет.  
  
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
