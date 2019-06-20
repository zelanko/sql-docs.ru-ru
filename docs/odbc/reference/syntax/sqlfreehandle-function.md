---
title: SQLFreeHandle, функция | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0ddaae66e60f77156b2d7c7e975875bb78d56cb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537331"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle, функция
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLFreeHandle** освобождает ресурсы, связанные с определенного дескриптора среды, подключения, инструкции или дескриптора.  
  
> [!NOTE]
>  Эта функция является универсальной функции за освобождение дескрипторов. Он заменяет функции ODBC 2.0 **SQLFreeConnect** (для освобождения дескриптора соединения) и **SQLFreeEnv** (для освобождения дескриптора среды). **SQLFreeConnect** и **SQLFreeEnv** устарели в ODBC 3 *.x*. **SQLFreeHandle** также заменяет функцию ODBC 2.0 **SQLFreeStmt** (с SQL_DROP *параметр*) за Освобождение дескриптора инструкции. Дополнительные сведения см. в разделе «Примечания». Дополнительные сведения о что диспетчер драйверов сопоставляет эту функцию, чтобы при ODBC 3 *.x* при работе с ODBC 2 *.x* драйвера, см. в разделе [сопоставление замещающих функций для назад Совместимость приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 [Вход] Тип дескриптора для освобождения **SQLFreeHandle**. Должен принимать одно из следующих значений:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 Дескриптор SQL_HANDLE_DBC_INFO_TOKEN используется только для диспетчера драйверов и драйверов. Приложения не должны использовать этот тип дескриптора. Дополнительные сведения о SQL_HANDLE_DBC_INFO_TOKEN, см. в разделе [драйвера ODBC с поддержкой пула подключений разработка](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Если *HandleType* не является одним из следующих значений **SQLFreeHandle** возвращает SQL_INVALID_HANDLE.  
  
 *Дескриптор*  
 [Вход] Дескриптор, который требуется освободить.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
 Если **SQLFreeHandle** возвращает значение SQL_ERROR, дескриптор все еще действителен.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLFreeHandle** возвращает значение SQL_ERROR, а связанное значение SQLSTATE может быть получен из структуры данных диагностики для дескриптора, **SQLFreeHandle** пытался выполнить бесплатно, но не удалось. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLFreeHandle** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимая для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) *HandleType* аргумент был SQL_HANDLE_ENV, и по крайней мере одно подключение был в состоянии выделением или подключенных. **SQLDisconnect** и **SQLFreeHandle** с *HandleType* из SQL_HANDLE_DBC должен вызываться для каждого подключения, перед вызовом **SQLFreeHandle** с *HandleType* из SQL_HANDLE_ENV.<br /><br /> (DM) *HandleType* аргумент был SQL_HANDLE_DBC, и что функция была вызвана перед вызовом **SQLDisconnect** для соединения.<br /><br /> (DM) *HandleType* аргумент был SQL_HANDLE_DBC. Асинхронно выполняемой функции был вызван с *обрабатывать* и функция по-прежнему выполняла при вызове этой функции.<br /><br /> (DM) *HandleType* аргумент имел значение SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван с дескриптором инструкции и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.<br /><br /> (DM) *HandleType* аргумент имел значение SQL_HANDLE_STMT. Асинхронно выполняемой функции был вызван для дескриптора инструкции или дескриптора связанного соединения, и функция по-прежнему выполняла при вызове этой функции.<br /><br /> (DM) *HandleType* аргумент был SQL_HANDLE_DESC. Асинхронно выполняемой функции был вызван в дескрипторе подключения; и функция по-прежнему выполняла при вызове этой функции.<br /><br /> (DM) все дочерние дескрипторы и другие ресурсы не были освобождены до **SQLFreeHandle** был вызван.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *обрабатывать* и *HandleType* было присвоено значение SQL_HANDLE_STMT или SQL_HANDLE_DESC возвращается SQL_PARAM_DATA_AVAILABLE. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|*HandleType* аргумент имел значение SQL_HANDLE_STMT или SQL_HANDLE_DESC и вызов функции не может быть обработан, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY017|Недопустимое использование автоматически выделенного дескриптора.|(DM) *обрабатывать* значение аргумента дескриптор автоматически выделенного дескриптора.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) *HandleType* аргумент SQL_HANDLE_DESC, и драйвер ODBC 2 *.x* драйвера.<br /><br /> (DM) *HandleType* аргумент имел значение SQL_HANDLE_STMT и что драйвер не был допустимым драйвер ODBC.|  
  
## <a name="comments"></a>Комментарии  
 **SQLFreeHandle** используется для освобождения дескрипторов для сред, соединений, инструкций и дескрипторов, как описано в следующих разделах. Общие сведения о маркерах см. в разделе [дескрипторы](../../../odbc/reference/develop-app/handles.md).  
  
 Приложения не следует использовать дескриптор, после ее освобождения; Диспетчер драйверов не проверяет допустимость дескриптора в вызове функции.  
  
## <a name="freeing-an-environment-handle"></a>Освобождение дескриптора среды  
 Перед вызовом **SQLFreeHandle** с *HandleType* SQL_HANDLE_ENV, приложение должно вызвать **SQLFreeHandle** с *HandleType*из SQL_HANDLE_DBC для всех подключений, выделенных в среде. В противном случае вызов **SQLFreeHandle** возвращает значение SQL_ERROR и среде и все активные соединения остается допустимым. Дополнительные сведения см. в разделе [эти задачи выполняет среда](../../../odbc/reference/develop-app/environment-handles.md) и [выделение маркер среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Если среда является совместно используемой среде, на приложение, которое вызывает **SQLFreeHandle** с *HandleType* SQL_HANDLE_ENV больше не имеет доступа к среде после вызова метода, но среды освобождение ресурсов не обязательно. Вызов **SQLFreeHandle** уменьшает счетчик ссылок среды. Счетчик ссылок поддерживается диспетчером драйверов. Если он не достигает нуля, общей среды не освобождается, так как он по-прежнему используется другим компонентом. Если число ссылок достигает нуля, освобождаются ресурсы общей среды.  
  
## <a name="freeing-a-connection-handle"></a>Освобождение дескриптора соединения  
 Перед вызовом **SQLFreeHandle** с *HandleType* SQL_HANDLE_DBC, приложение должно вызвать **SQLDisconnect** для подключения, если имеется соединение на это обрабатывать *.* В противном случае вызов **SQLFreeHandle** возвращает значение SQL_ERROR и подключение остается допустимым.  
  
 Дополнительные сведения см. в разделе [дескрипторы соединений](../../../odbc/reference/develop-app/connection-handles.md) и [отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции  
 Вызов **SQLFreeHandle** с *HandleType* значение SQL_HANDLE_STMT освобождает все ресурсы, которые были выделены с помощью вызова **SQLAllocHandle** с  *HandleType* значение SQL_HANDLE_STMT. Если приложение вызывает **SQLFreeHandle** чтобы освободить инструкцию с ожидающими результатов, ожидающих результаты будут удалены. Когда приложение освобождает дескриптор инструкции, драйвер освобождает четыре автоматически выделенные дескрипторы, связанные с этот дескриптор. Дополнительные сведения см. в разделе [оператор обрабатывает](../../../odbc/reference/develop-app/statement-handles.md) и [освободить дескриптор инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Обратите внимание, что **SQLDisconnect** автоматически удаляет все инструкции и открытые дескрипторы для соединения.  
  
## <a name="freeing-a-descriptor-handle"></a>Освобождение дескриптора дескриптора  
 Вызов **SQLFreeHandle** с *HandleType* из SQL_HANDLE_DESC освобождает дескриптор в *обрабатывать*. Вызов **SQLFreeHandle** не освобождает память, выделенная приложение, которое может ссылаться на поле указателя (включая SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR) любого запись с дескриптора объекта *обрабатывать*. Объем памяти, выделенной с помощью драйвера для полей, которые не являются полями указателя освобождается при освобождении дескриптора. При освобождении дескриптора, выделяемый пользователем, все инструкции, освобожденные дескриптор связано с вернуться к их соответствующих автоматически выделенного дескриптора.  
  
> [!NOTE]
>  ODBC 2 *.x* драйверы не поддерживают освобождения дескриптора, так же, как они не поддерживают выделения дескриптора.  
  
 Обратите внимание, что **SQLDisconnect** автоматически удаляет все инструкции и открытые дескрипторы для соединения. Когда приложение освобождает дескриптор инструкции, драйвер освобождает все автоматически созданные дескрипторов, связанных с этот дескриптор.  
  
 Дополнительные сведения о дескрипторах, см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Пример кода  
 Дополнительные примеры кода, см. в разделе [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
### <a name="code"></a>Код  
  
```cpp  
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
|Отмена обработка инструкций|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Задав имя курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы ODBC](../../../odbc/reference/sample-odbc-program.md)
