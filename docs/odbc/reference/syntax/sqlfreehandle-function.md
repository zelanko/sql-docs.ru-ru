---
title: "SQLFreeHandle, функция | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd53996a8107a577cfae703a8f68f036e5ae0eb6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle, функция
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLFreeHandle** освобождает ресурсы, связанные с определенного дескриптора среды, соединения, оператор или дескриптора.  
  
> [!NOTE]  
>  Эта функция является универсальной функции освобождения дескрипторов. Он заменяет функции ODBC 2.0 **SQLFreeConnect** (для освобождения дескриптора соединения) и **SQLFreeEnv** (для освобождения дескриптора среды). **SQLFreeConnect** и **SQLFreeEnv** устарели в ODBC 3*.x*. **SQLFreeHandle** также заменяет функцию ODBC 2.0 **SQLFreeStmt** (с SQL_DROP *параметр*) для освобождения дескриптора инструкции. Дополнительные сведения см. в разделе «Комментарии». Дополнительные сведения о том, что диспетчер драйверов преобразует эту функцию для при ODBC 3*.x* при работе с ODBC 2*.x* драйвера, в разделе [сопоставление замены функции для назад Совместимость приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 [Вход] Тип дескриптор для освобождения **SQLFreeHandle**. Должен быть одним из следующих значений:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   ЗНАЧЕНИЕ SQL_HANDLE_STMT  
  
 Дескриптор SQL_HANDLE_DBC_INFO_TOKEN используется только для диспетчера драйверов и драйверов. Приложения не должны использовать этот тип дескриптора. Дополнительные сведения о SQL_HANDLE_DBC_INFO_TOKEN см. в разделе [разработке пула соединений, поддерживающие драйвер ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Если *HandleType* не является одним из следующих значений **SQLFreeHandle** возвращает SQL_INVALID_HANDLE.  
  
 *Дескриптор*  
 [Вход] Дескриптор для освобождения.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
 Если **SQLFreeHandle** возвращает значение SQL_ERROR, дескриптор все еще действительна.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLFreeHandle** возвращает значение SQL_ERROR, соответствующее значение SQLSTATE может быть получен из структуры данных диагностики для дескриптора, **SQLFreeHandle** попытка освободить, но не удалось. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLFreeHandle** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в * \*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) *HandleType* аргумент был SQL_HANDLE_ENV, и хотя бы одно подключение находился в состоянии выделенной или подключенной. **SQLDisconnect** и **SQLFreeHandle** с *HandleType* установленным в значение sql_handle_dbc должен вызываться для каждого соединения перед вызовом **SQLFreeHandle** с *HandleType* установленным в значение sql_handle_env.<br /><br /> (DM) *HandleType* аргумент был SQL_HANDLE_DBC, и вызове функции перед вызовом **SQLDisconnect** для соединения.<br /><br /> (DM) *HandleType* аргумент был SQL_HANDLE_DBC. Асинхронно выполняемой функции был вызван с *обработки* и функция выполнялась по-прежнему при вызове этой функции.<br /><br /> (DM) *HandleType* аргумент имеет значение SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван с дескриптором инструкции и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.<br /><br /> (DM) *HandleType* аргумент имеет значение SQL_HANDLE_STMT. Асинхронно выполняемой функции был вызван для дескриптора инструкции или дескриптором связанного соединения и функция выполнялась по-прежнему при вызове этой функции.<br /><br /> (DM) *HandleType* аргумент был SQL_HANDLE_DESC. Асинхронно выполняемой функции был вызван с дескриптором связанного соединения; и функция выполнялась по-прежнему при вызове этой функции.<br /><br /> (DM) все их дочерние дескрипторы и другие ресурсы не были выпущены до **SQLFreeHandle** был вызван.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *обработки* и *HandleType* было присвоено значение SQL_HANDLE_STMT или SQL_HANDLE_DESC возвращается SQL_PARAM_DATA_AVAILABLE. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|*HandleType* аргумент имеет значение SQL_HANDLE_STMT или SQL_HANDLE_DESC, а вызов функции не может быть обработан, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY017|Недопустимое использование автоматически выделенного дескриптора.|(DM) *обработки* значение аргумента дескриптор автоматически выделенного дескриптора.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) *HandleType* аргумент SQL_HANDLE_DESC, и драйвер ODBC 2*.x* драйвера.<br /><br /> (DM) *HandleType* аргумент имеет значение SQL_HANDLE_STMT и драйвер не является допустимым драйвером ODBC.|  
  
## <a name="comments"></a>Комментарии  
 **SQLFreeHandle** используется для освобождения дескрипторов для сред, соединений, инструкций и дескрипторов, как описано в следующих разделах. Общие сведения о маркерах см. в разделе [дескрипторов](../../../odbc/reference/develop-app/handles.md).  
  
 Приложение не следует использовать дескриптор после ее освобождения; Диспетчер драйверов не проверяет допустимость дескриптора в вызове функции.  
  
## <a name="freeing-an-environment-handle"></a>Освобождение дескриптора среды  
 Перед вызовом **SQLFreeHandle** с *HandleType* установленным в значение sql_handle_env, приложение должно вызвать **SQLFreeHandle** с *HandleType*установленным в значение sql_handle_dbc для всех подключений, выделенное в среде. В противном случае вызов **SQLFreeHandle** возвращает значение SQL_ERROR и среды и все активные соединения остается действительным. Дополнительные сведения см. в разделе [обрабатывает среды](../../../odbc/reference/develop-app/environment-handles.md) и [выделения памяти для обработки среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Если среда находится в общей среде, на приложение, которое вызывает **SQLFreeHandle** с *HandleType* установленным в значение sql_handle_env больше не имеет доступа к среде после вызова метода, но среда освобождение ресурсов не обязательно. Вызов **SQLFreeHandle** уменьшает число ссылок среды. Счетчик ссылок поддерживается диспетчером драйверов. Если он не достигает нуля, общей среды не освобождается, так как он по-прежнему используется другим компонентом. Если число ссылок достигает нуля, освобождаются ресурсы общей среды.  
  
## <a name="freeing-a-connection-handle"></a>Освобождение дескриптора соединения  
 Перед вызовом **SQLFreeHandle** с *HandleType* SQL_HANDLE_DBC, приложение должно вызвать **SQLDisconnect** для подключения, если имеется соединение в данном обрабатывать*.* В противном случае вызов **SQLFreeHandle** возвращает значение SQL_ERROR и соединение остается действительным.  
  
 Дополнительные сведения см. в разделе [соединений обрабатывает](../../../odbc/reference/develop-app/connection-handles.md) и [отключение от источника данных или драйвер](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции  
 Вызов **SQLFreeHandle** с *HandleType* значение sql_handle_stmt освобождает все ресурсы, выделенные с помощью вызова **SQLAllocHandle** с * HandleType* значение sql_handle_stmt. Если приложение вызывает **SQLFreeHandle** освободить инструкцию с ожидающими результатами, ожидающие результаты удаляются. Когда приложение освобождает дескриптор инструкции, драйвер освобождает четыре автоматически выделенного дескрипторов, связанных с этот дескриптор. Дополнительные сведения см. в разделе [оператор обрабатывает](../../../odbc/reference/develop-app/statement-handles.md) и [освободить дескриптор инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Обратите внимание, что **SQLDisconnect** автоматически удаляет любые инструкции и открытые дескрипторы для соединения.  
  
## <a name="freeing-a-descriptor-handle"></a>Освобождение дескриптора  
 Вызов **SQLFreeHandle** с *HandleType* из SQL_HANDLE_DESC освобождает дескриптор в *обработки*. Вызов **SQLFreeHandle** любого не освобождает память, выделенная программой, которая может быть связан с полем указателя (включая SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR) запись дескриптора *обработки*. Объем памяти, выделенный с помощью драйвера для полей, которые не являются полями указатель освобождается при освобождении дескриптора. При освобождении дескриптора выделенный пользователем всех инструкций, освобожденные дескриптор связано с вернуться к их соответствующих автоматически выделенного дескриптора.  
  
> [!NOTE]  
>  ODBC 2*.x* драйверы не поддерживают освобождения дескриптора, так же, как они не поддерживают выделение дескриптора.  
  
 Обратите внимание, что **SQLDisconnect** автоматически удаляет любые инструкции и открытые дескрипторы для соединения. Когда приложение освобождает дескриптор инструкции, драйвер освобождает автоматически созданный дескрипторов, связанных с этот дескриптор.  
  
 Дополнительные сведения о дескрипторах см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Пример кода  
 Дополнительные примеры кода, в разделе [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
### <a name="code"></a>код  
  
```  
// SQLFreeHandle.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <stdio.h>  
  
int main() {  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   // Initialize the environment, connection, statement handles.  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   // Allocate the environment.  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set environment attributes.  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
  
   // Allocate the connection.  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Set the login timeout.  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
  
   // Let the user select the data source and connect to the database.  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Free handles, and disconnect.     
   if (hstmt) {   
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
      hstmt = NULL;   
   }  
   if (hdbc) {   
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      hdbc = NULL;   
   }  
   if (henv) {   
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
      henv = NULL;   
   }  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выделение дескриптора|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Отмена обработки инструкции|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Имя курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовка ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы на ODBC](../../../odbc/reference/sample-odbc-program.md)
