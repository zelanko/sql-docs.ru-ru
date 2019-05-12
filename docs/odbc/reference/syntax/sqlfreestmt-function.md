---
title: SQLFreeStmt, функция | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ff8cb5bd0ff257d42cd658da54415697e99ae0f
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538148"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt, функция
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLFreeStmt** останавливает обработку, связанные с определенной инструкции, закрывает все открытые курсоры, связанных с инструкцией, пустые переменные результатов, ожидающих обработки или, при необходимости, освобождает все ресурсы, связанные с дескриптором инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции  
  
 *Параметр*  
 [Вход] Один из следующих вариантов:  
  
 ЗАКРЫТЬ SQL_: Закрывает курсор, связанный с *StatementHandle* (если они были определены) и отменяет все ожидающие результаты. Приложения можно повторно открыть этот курсор позже, выполнив **ВЫБЕРИТЕ** инструкцию с значения одной или разных параметров. Если никакой курсор открыт, этот параметр не действует для приложения. **SQLCloseCursor** также можно вызывать закрытии курсора. Дополнительные сведения см. в разделе [закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Этот параметр является устаревшим. Вызов **SQLFreeStmt** с *параметр* из SQL_DROP сопоставлен диспетчера драйверов для [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
 SQL_UNBIND: Задает поле SQL_DESC_COUNT Отменить 0, освобождение всех буферах столбцов, привязанную с **SQLBindCol** для заданного *StatementHandle*. Это не отменить привязку столбца закладки; Чтобы сделать это, поле SQL_DESC_DATA_PTR Отменить для столбца закладок присваивается значение NULL. Обратите внимание на то, что если эта операция выполняется на явно выделенные дескриптора, который является общим для нескольких инструкций, операция будет влиять на привязки для всех инструкций, которые совместно используют дескриптора. Дополнительные сведения см. в разделе [Обзор из извлечение результатов (базовые)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Задает поле SQL_DESC_COUNT APD 0, освобождая все буферы параметра задается **SQLBindParameter** для заданного *StatementHandle*. Если эта операция выполняется на явно выделенные дескриптора, который является общим для нескольких инструкций, эта операция повлияет на все инструкции, которые совместно используют дескриптор привязки. Дополнительные сведения см. в разделе [привязка параметров](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLFreeStmt** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLFreeStmt** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLFreeStmt** был вызван.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Эта функция была вызвана с *параметр* в значение SQL_RESET_PARAMS до получения для всех параметров потоковых данных.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY092|Тип параметра за пределами диапазона|(DM) значение, указанное для аргумента *параметр* не:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов **SQLFreeStmt** с SQL_CLOSE параметр эквивалентно вызову **SQLCloseCursor**, за исключением того, что **SQLFreeStmt** с SQL_CLOSE не влияет на приложения Если никакой курсор открыт в операторе. Если нет открытие, вызов **SQLCloseCursor** возвращает SQLSTATE 24000 (недопустимое состояние курсора).  
  
 Приложения не следует использовать дескриптор инструкции после ее освобождения; Диспетчер драйверов не проверяет допустимость дескриптора в вызове функции.  
  
## <a name="example"></a>Пример  
 Он является хорошим стилем программирования для освобождения дескрипторов. Однако для простоты, следующий пример не включает код, который освобождает выделенные дескрипторы. Пример для освобождения дескрипторов, см. в разделе [SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
```cpp  
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
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Закрытие курсора|[Функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Освобождение дескриптора|[Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Задав имя курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
