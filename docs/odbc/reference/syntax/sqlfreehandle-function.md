---
title: Функция SQLFreeHandle | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e312bcbc6efcb96ff02657b98034f0340ae377dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68345183"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,0: ISO 92  
  
 **Сводка**  
 **SQLFreeHandle** освобождает ресурсы, связанные с определенной средой, соединением, инструкцией или дескриптором дескриптора.  
  
> [!NOTE]
>  Эта функция является универсальной функцией для освобождения дескрипторов. Он заменяет функции ODBC 2,0 **SQLFreeConnect** (для освобождения маркера подключения) и **SQLFreeEnv** (для освобождения обработчика среды). **SQLFreeConnect** и **SQLFreeEnv** являются устаревшими в ODBC 3 *. x*. **SQLFreeHandle** также заменяет функцию ODBC 2,0 **SQLFreeStmt** (с *параметром*SQL_DROP) для освобождения маркера инструкции. Дополнительные сведения см. в разделе "Комментарии". Дополнительные сведения о том, как диспетчер драйверов сопоставляет эту функцию, когда приложение ODBC 3 *. x* работает с драйвером ODBC 2 *. x* , см. в разделе [Сопоставление функций замены для обратной совместимости приложений](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 Входной Тип обработчика, освобождаемый **SQLFreeHandle**. Необходимо установить одно из следующих значений.  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKENный обработчик используется только диспетчером драйверов и драйвером. Приложения не должны использовать этот тип обработчика. Дополнительные сведения о SQL_HANDLE_DBC_INFO_TOKEN см. [в разделе Разработка осведомленности о пуле подключений в драйвере ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Если *параметром handletype* не является одним из этих значений, **SQLFreeHandle** возвращает SQL_INVALID_HANDLE.  
  
 *Справиться*  
 Входной Освобождаемый обработчик.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_ERROR или SQL_INVALID_HANDLE.  
  
 Если **SQLFreeHandle** возвращает SQL_ERROR, маркер по-прежнему является допустимым.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLFreeHandle** возвращает SQL_ERROR, связанное значение SQLSTATE может быть получено из структуры диагностических данных для маркера, который **SQLFreeHandle** пытался освободить, но не может. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLFreeHandle** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) аргумент *параметром handletype* был SQL_HANDLE_ENV, и по крайней мере одно подключение находилось в выделенном или подключенном состоянии. **SQLDisconnect** и **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DBC должны вызываться для каждого подключения перед вызовом **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_ENV.<br /><br /> (DM) аргумент *параметром handletype* был SQL_HANDLE_DBC, а функция вызывалась до вызова **SQLDisconnect** для соединения.<br /><br /> (DM) аргумент *параметром handletype* был SQL_HANDLE_DBC. Асинхронно исполняемая функция была вызвана с помощью *Handle* , а функция все еще выполнялась при вызове этой функции.<br /><br /> (DM) аргумент *параметром handletype* был SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны с маркером инструкции и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.<br /><br /> (DM) аргумент *параметром handletype* был SQL_HANDLE_STMT. В обработчике инструкции или связанном обработчике соединения была вызвана асинхронно исполняемая функция, а функция все еще выполнялась при вызове этой функции.<br /><br /> (DM) аргумент *параметром handletype* был SQL_HANDLE_DESC. В связанном обработчике соединения вызвана асинхронно исполняемая функция; и функция все еще выполнялась при вызове этой функции.<br /><br /> (DM) все дескрипторы дочерних подразделений и другие ресурсы не были освобождены до вызова **SQLFreeHandle** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *дескриптором* , а *параметром handletype* был установлен в SQL_HANDLE_STMT или SQL_HANDLE_DESC возвращен SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Аргумент *параметром handletype* был SQL_HANDLE_STMT или SQL_HANDLE_DESC, и вызов функции не может быть обработан, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за условий нехватки памяти.|  
|HY017|Недопустимое использование автоматически выделенного дескриптора дескриптора.|(DM) аргумент *дескриптора* был задан дескриптором для автоматически выделенного дескриптора.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) аргумент *параметром handletype* был SQL_HANDLE_DESC, а драйвер — драйвер ODBC 2 *. x* .<br /><br /> (DM) аргумент *параметром handletype* был SQL_HANDLE_STMT, а драйвер не является допустимым драйвером ODBC.|  
  
## <a name="comments"></a>Комментарии  
 **SQLFreeHandle** используется для освобождения дескрипторов для сред, соединений, инструкций и дескрипторов, как описано в следующих разделах. Общие сведения об дескрипторах см. в разделе [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Приложение не должно использовать обработчик после его освобождения; Диспетчер драйверов не проверяет допустимость маркера в вызове функции.  
  
## <a name="freeing-an-environment-handle"></a>Освобождение обработчика среды  
 Прежде чем вызывать **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_ENV, приложение должно вызвать **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DBC для всех подключений, выделенных в среде. В противном случае вызов **SQLFreeHandle** возвращает значение SQL_ERROR, и среда и все активные соединения остаются действительными. Дополнительные сведения см. в разделе [дескрипторы среды](../../../odbc/reference/develop-app/environment-handles.md) и [Выделение дескриптора среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Если среда является общей, приложение, вызывающее **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_ENV, больше не имеет доступа к среде после вызова, но ресурсы среды не обязательно освобождаются. Вызов **SQLFreeHandle** уменьшает число ссылок в среде. Счетчик ссылок поддерживается диспетчером драйверов. Если он не достигает нуля, то общая среда не освобождается, так как она по-прежнему используется другим компонентом. Если счетчик ссылок достигает нуля, ресурсы общей среды освобождаются.  
  
## <a name="freeing-a-connection-handle"></a>Освобождение маркера подключения  
 Прежде чем вызывать **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DBC, приложение должно вызвать **SQLDisconnect** для соединения, если имеется соединение с этим обработчиком *.* В противном случае вызов **SQLFreeHandle** возвращает SQL_ERROR, а соединение остается действительным.  
  
 Дополнительные сведения см. в разделе [дескрипторы соединения](../../../odbc/reference/develop-app/connection-handles.md) и [Отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции  
 Вызов **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_STMT освобождает все ресурсы, выделенные вызовом **функцию SQLAllocHandle** с *параметром handletype* SQL_HANDLE_STMT. Когда приложение вызывает **SQLFreeHandle** для освобождения инструкции с ожидающими результатами, ожидающие результаты удаляются. Когда приложение освобождает дескриптор инструкции, драйвер освобождает четыре автоматически выделяемых дескрипторов, связанных с этим дескриптором. Дополнительные сведения см. в разделе [дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md) и [освобождение дескриптора инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Обратите внимание, что **SQLDisconnect** автоматически удаляет любые инструкции и дескрипторы, открытые в соединении.  
  
## <a name="freeing-a-descriptor-handle"></a>Освобождение дескриптора дескриптора  
 Вызов **SQLFreeHandle** с *параметром handletype* SQL_HANDLE_DESC освобождает дескриптор дескриптора в *дескрипторе*. Вызов **SQLFreeHandle** не освобождает память, выделенную приложением, на которое может ссылаться поле указателя (в том числе SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR) любой записи дескриптора *дескриптора*. Память, выделенная драйвером для полей, не являющихся полями указателя, освобождается при освобождении маркера. При освобождении дескриптора, выделенного пользователем, все инструкции, с которыми был связан освобожденный дескриптор, возвращаются к соответствующим автоматически выделенным дескрипторам дескрипторов.  
  
> [!NOTE]
>  Драйверы ODBC 2 *. x* не поддерживают дескрипторы освобождения дескрипторов, так как они не поддерживают распределение дескрипторов.  
  
 Обратите внимание, что **SQLDisconnect** автоматически удаляет любые инструкции и дескрипторы, открытые в соединении. Когда приложение освобождает дескриптор инструкции, драйвер освобождает все автоматически создаваемые дескрипторы, связанные с этим дескриптором.  
  
 Дополнительные сведения о дескрипторах см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Пример кода  
 Дополнительные примеры кода см. в разделе [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
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
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Выделение маркера|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Отмена обработки инструкции|[Склканце, функция](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Задание имени курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы ODBC](../../../odbc/reference/sample-odbc-program.md)
