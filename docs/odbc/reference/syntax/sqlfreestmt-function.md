---
title: Функция SQLFreeStmt | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f2f3e9021732f7d6b58e4d14641ae7874bf4c4e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt, функция
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLFreeStmt** останавливает обработку, связанные с определенной инструкции, закрывает все открытые курсоры, связанные с инструкцией, удаляет результатов, ожидающих обработки, а при необходимости освобождает все ресурсы, связанные с дескриптором инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции  
  
 *Параметр*  
 [Вход] Один из следующих вариантов:  
  
 ЗАКРЫТЬ SQL_: Закрывает курсор, связанный с *StatementHandle* (если они были определены) и отменяет все ожидающие результаты. Приложение можно открыть этот курсор более поздней версии, выполнив **ВЫБЕРИТЕ** инструкцию с значения одной или разных параметров. Если никакой курсор открыт, этот параметр не оказывает влияния для приложения. **SQLCloseCursor** также можно вызвать для закрытия курсора. Дополнительные сведения см. в разделе [закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Этот параметр устарел. Вызов **SQLFreeStmt** с *параметр* из SQL_DROP сопоставленного диспетчера драйверов для [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
 SQL_UNBIND: Наборы поле SQL_DESC_COUNT Отменить 0, освобождая все буферы столбец связан с **SQLBindCol** для данного *StatementHandle*. Это не отменить привязку закладку для столбца; Чтобы сделать это, поле SQL_DESC_DATA_PTR Отменить для столбца закладок будет равно NULL. Обратите внимание, что эта операция выполняется на явно выделенного дескриптора, который является общим для нескольких инструкций, операцию влияет на привязки для всех инструкций, которые совместно используют дескриптора. Дополнительные сведения см. в разделе [Обзор для получения результатов (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Задает поле SQL_DESC_COUNT APD 0, освобождая все буферы параметра задается **SQLBindParameter** для данного *StatementHandle*. Если эта операция выполняется на явно выделенного дескриптора, который является общим для нескольких инструкций, эта операция влияет на привязки для всех инструкций, которые совместно используют дескриптора. Дополнительные сведения см. в разделе [привязка параметров](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLFreeStmt** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLFreeStmt** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLFreeStmt** был вызван.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. Эта функция была вызвана с *параметр* перед получения данных для всех параметров потоковой установлен в значение SQL_RESET_PARAMS.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY092|Тип параметра за пределами диапазона|(DM) значение, указанное для аргумента *параметр* не был:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов **SQLFreeStmt** с SQL_CLOSE параметр эквивалентно вызову **SQLCloseCursor**, за исключением того, что **SQLFreeStmt** с SQL_CLOSE не влияет на приложения Если никакой курсор открыт в инструкции. Если никакой курсор откройте, вызов **SQLCloseCursor** возвращает SQLSTATE 24000 (недопустимое состояние курсора).  
  
 Приложение не следует использовать дескриптор инструкции после ее освобождения; Диспетчер драйверов не проверяет допустимость дескриптора в вызове функции.  
  
## <a name="example"></a>Пример  
 Это хороший стиль программирования для освобождения дескрипторов. Однако для простоты следующий пример не включает код, который освобождает выделенной дескрипторов. Пример освободить дескрипторы см [SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
```  
// SQLFreeStmt.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
   retCode = SQLFreeStmt(hstmt, SQL_UNBIND);  
   retCode = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выделение дескриптора|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Закрытие курсора|[Функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Освобождение дескриптора|[Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Имя курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
