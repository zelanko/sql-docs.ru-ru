---
title: Функция S'LFreeHandle (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b136dec98a19676aa67c78615d8fe931f62aafa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285775"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle, функция
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 3.0: ISO 92  
  
 **Сводка**  
 **SLFreeHandle** освобождает ресурсы, связанные с определенной средой, соединением, операторами или дескрипторной ручкой.  
  
> [!NOTE]
>  Эта функция является общей функцией для освобождения ручек. Он заменяет функции ODBC 2.0 **s'LFreeConnect** (для освобождения ручки соединения) и **S'LFreeEnv** (для освобождения ручки среды). **В** ODBC 3 *.x*обе страны были обесцвечены и **s'LFreeEnv.** **Кроме** того, функция ODBC 2.0 заменяет функцию ODBC 2.0 **s'LFreeStmt** (с SQL_DROP *вариантом)* для освобождения ручки оператора. Для получения дополнительной информации см. Для получения дополнительной информации о том, что менеджер *.x* драйвера драйвера драйвера *.x* управления драйвером, [см.](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HandleType*  
 (Вход) Тип ручки, который будет освобожден **s'LFreeHandle**. Необходимо установить одно из следующих значений.  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ручка используется только менеджером водителя и водителем. Приложения не должны использовать этот тип рукоятки. Для получения дополнительной информации о SQL_HANDLE_DBC_INFO_TOKEN [см.](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)  
  
 Если *HandleType* не является одним из этих значений, **s'LFreeHandle** возвращается SQL_INVALID_HANDLE.  
  
 *Дескриптор*  
 (Вход) Ручка, чтобы быть освобождены.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_ERROR или SQL_INVALID_HANDLE.  
  
 Если SQL_ERROR возвращается **SQL_ERROR,** ручка по-прежнему действительна.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **sLFreeHandle** возвращается SQL_ERROR, связанное с этим значение S'LSTATE может быть получено из структуры диагностических данных для ручки, которую **S'LFreeHandle** пытался освободить, но не смог. В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LFreeHandle,** и разъясняется каждая из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) Аргумент *HandleType* был SQL_HANDLE_ENV, и по крайней мере одно соединение находилось в выделенном или подключенном состоянии. **Перед** *вызовом* **S'LFreeHandle** и **S'LFreeHandle** с *помощью handleType* SQL_HANDLE_DBC необходимо вызывать для каждого соединения, прежде чем звонить в SQL_HANDLE_ENV.<br /><br /> (DM) Аргумент *HandleType* был SQL_HANDLE_DBC, и функция была вызвана до вызова **S'LDisconnect** для соединения.<br /><br /> (DM) Аргумент *HandleType* был SQL_HANDLE_DBC. Асинхронно исполняющая функция была вызвана с *помощью Handle,* и функция все еще исполнялась, когда эта функция была вызвана.<br /><br /> (DM) Аргумент *HandleType* был SQL_HANDLE_STMT. **С помощью**ручки оператора **SQLBulkOperations** **была** вызвана с помощью ручки оператора и возвращена SQL_NEED_DATA. **SQLExecDirect** Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.<br /><br /> (DM) Аргумент *HandleType* был SQL_HANDLE_STMT. Асинхронно исполняющая функция была вызвана на ручку оператора или на связанную ручку соединения, и функция все еще исполнялась, когда эта функция была вызвана.<br /><br /> (DM) Аргумент *HandleType* был SQL_HANDLE_DESC. На связанной ручке соединения была вызвана асинхронно исполнительная функция; и функция по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) Все вспомогательные ручки и другие ресурсы не были выпущены до того, как был вызван **S'LFreeHandle.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для одной из декретов оператора, связанных с *ручкой* и *HandleType* был установлен SQL_HANDLE_STMT или SQL_HANDLE_DESC возвращен SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Аргумент *HandleType* был SQL_HANDLE_STMT или SQL_HANDLE_DESC, и вызов функции не мог быть обработан, потому что основные объекты памяти не могли быть доступны, возможно, из-за низких условий памяти.|  
|HY017|Недействительное использование автоматически выделенной дескриптора.|(DM) Аргумент *Ручка* был установлен на ручку для автоматически выделенного дескриптора.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Аргумент *HandleType* был SQL_HANDLE_DESC, и водитель был водителем ODBC 2 *.x.*<br /><br /> (DM) Аргумент *HandleType* был SQL_HANDLE_STMT, и водитель не был действительным драйвером ODBC.|  
  
## <a name="comments"></a>Комментарии  
 **СЗЛФриМорд** используется для бесплатных ручек для сред, соединений, инструкций и дескрипторов, как описано в следующих разделах. Для получения общей информации [Handles](../../../odbc/reference/develop-app/handles.md)о ручках см.  
  
 Приложение не должно использовать ручку после его освобождения; Менеджер драйвера не проверяет достоверность ручки в вызове функции.  
  
## <a name="freeing-an-environment-handle"></a>Освобождение окружающей среды Ручка  
 Перед тем, как вызвать **s'LFreeHandle** с *помощью SQL_HANDLE_ENV,* приложение должно вызвать **s'LFreeHandle** с *SQL_HANDLE_DBC HandleType* для всех подключений, выделенных в среде. В противном случае, вызов на **S'LFreeHandle** возвращается SQL_ERROR и среды и любого активного соединения остается действительным. Для получения дополнительной [информации](../../../odbc/reference/develop-app/environment-handles.md) [Allocating the Environment Handle](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)см.  
  
 Если среда является общей средой, приложение, вызываевшее **S'LFreeHandle** с *помощью HandleType* SQL_HANDLE_ENV больше не имеет доступа к среде после вызова, но ресурсы среды не обязательно освобождаются. Призыв к **S'LFreeHandle** приспозывает количество ссылок на окружающую среду. Подсчет ссылок поддерживается менеджером драйверов. Если она не достигает нуля, общая среда не освобождается, поскольку она по-прежнему используется другим компонентом. Если количество ссылок достигает нуля, ресурсы общей среды освобождаются.  
  
## <a name="freeing-a-connection-handle"></a>Освобождение ручки соединения  
 Перед тем, как вызвать **s'LFreeHandle** с *помощью SQL_HANDLE_DBC,* приложение должно вызвать **S'LDisconnect** для подключения, если на этой ручке есть*подключение.* В противном случае вызов на **sLFreeHandle** возвращается SQL_ERROR и соединение остается действительным.  
  
 Для получения дополнительной информации см. [Ручки подключения](../../../odbc/reference/develop-app/connection-handles.md) и [отключение от источника данных или драйвера](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Освобождение дескриптора инструкции  
 Звонок в **S'LFreeHandle** с *помощью* SQL_HANDLE_STMT освобождает все ресурсы, выделенные по вызову **в S'LAllocHandle** с SQL_HANDLE_STMT *помощью.* Когда приложение вызывает **S'LFreeHandle,** чтобы освободить выписку, которая не достигла результатов, ожидающие результаты удаляются. Когда приложение освобождает ручку оператора, драйвер освобождает четыре автоматически выделенных дескриптора, связанных с этой ручкой. Для получения дополнительной [информации](../../../odbc/reference/develop-app/statement-handles.md) [Freeing a Statement Handle](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)см.  
  
 Обратите внимание на то, что **S'LDisconnect** автоматически отбрасывает все операторы и дескрипторы, открытые на подключении.  
  
## <a name="freeing-a-descriptor-handle"></a>Освобождение дескриптора Ручка  
 Звонок на **s'LFreeHandle** с *помощью HandleType* SQL_HANDLE_DESC освобождает ручку дескриптора в *ручке.* Вызов на **sLFreeHandle** не выпускает памяти, выделенной приложением, на которую может ссылаться поле указателя (включая SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR) любой дескрипторной записи *Handle.* Память, выделенная драйвером для полей, не отображаемых полями указателей, освобождается при освобождении ручки. При освобождении дескриптора, выделенного пользователем, все операторы, которые высвободившиеся ручки были связаны с возвратом к их соответствующим автоматически выделенным дескрипторам.  
  
> [!NOTE]
>  Драйверы ODBC 2 *.x* не поддерживают дескрипторные ручки, так же как они не поддерживают выделение дескрипторов.  
  
 Обратите внимание на то, что **S'LDisconnect** автоматически отбрасывает все операторы и дескрипторы, открытые на подключении. Когда приложение освобождает ручку оператора, драйвер освобождает все автоматически генерируемые дескрипторы, связанные с этой ручкой.  
  
 Для получения дополнительной информации о [Descriptors](../../../odbc/reference/develop-app/descriptors.md)дескрипторах см.  
  
## <a name="code-example"></a>Пример кода  
 Дополнительные образцы кода можно узнать по видам кода и [веб-кодам s'LBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [S'LConnect.](../../../odbc/reference/syntax/sqlconnect-function.md)  
  
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
|Выделение ручки|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Отмена обработки оператора|[Функционер СЗЛКанс](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Установка имени курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовка ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Образец программы ODBC](../../../odbc/reference/sample-odbc-program.md)
