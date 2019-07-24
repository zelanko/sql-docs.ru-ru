---
title: Функция SQLFreeStmt | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6141f3efe357bfb3f14c04aa2f6760e9470649a6
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345145"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt, функция
**Соответствия**  
 Представленная версия: Соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLFreeStmt** прекращает обработку, связанную с определенной инструкцией, закрывает все открытые курсоры, связанные с инструкцией, отменяет ожидающие результаты или, при необходимости, освобождает все ресурсы, связанные с этим маркером инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции  
  
 *Параметр*  
 Входной Один из следующих вариантов:  
  
 SQL_ ЗАКРЫТЬ: Закрывает курсор, связанный с *статеменсандле* (если он был определен), и отменяет все ожидающие результаты. Приложение может снова открыть этот курсор позже, повторно выполнив инструкцию **SELECT** с теми же или другими значениями параметров. Если курсор не открыт, этот параметр не влияет на приложение. **SQLCloseCursor** также можно вызвать для закрытия курсора. Дополнительные сведения см. [в разделе заключение курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Этот параметр является устаревшим. Вызов **SQLFreeStmt** с ПАРАМЕТРом SQL_DROP  сопоставляется в диспетчере драйверов с [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
 SQL_UNBIND: Задает для поля SQL_DESC_COUNT АРД значение 0, освобождая все буферы столбцов, привязанные **SQLBindCol** для данного *статеменсандле*. Это не приводит к отмене привязки столбца Bookmark. для этого в поле SQL_DESC_DATA_PTR АРД для столбца Bookmark устанавливается значение NULL. Обратите внимание, что если эта операция выполняется для явно выделенного дескриптора, совместно используемого более чем одной инструкцией, операция повлияет на привязки всех инструкций, совместно использующих этот дескриптор. Дополнительные сведения см. в разделе [Обзор получения результатов (базовый)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Задает для поля SQL_DESC_COUNT APD значение 0, освобождая все буферы параметров, установленные **SQLBindParameter** для данного *статеменсандле*. Если эта операция выполняется для явно выделенного дескриптора, совместно используемого более чем одной инструкцией, эта операция повлияет на привязки всех инструкций, совместно использующих этот дескриптор. Дополнительные сведения см. в разделе [Параметры привязки](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLFreeStmt** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и маркером  *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLFreeStmt** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией  *\** **SQLGetDiagRec** в буфере MessageText, описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове **SQLFreeStmt** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана  с параметром, ИМЕЮЩИМ значение SQL_RESET_PARAMS до получения данных для всех потоковых параметров.<br /><br /> (DM) была вызвана асинхронно исполняемая функция для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращенного SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY092|Тип параметра вне допустимого диапазона|(DM) значение, указанное для *параметра* Argument, не было:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов **SQLFreeStmt** с параметром SQL_CLOSE эквивалентен вызову **SQLCloseCursor**, за исключением того, что **SQLFreeStmt** с SQL_CLOSE не влияет на приложение, если в инструкции не открыт курсор. Если курсор не открыт, вызов **SQLCloseCursor** ВОЗВРАЩАЕТ значение SQLSTATE 24000 (недопустимое состояние курсора).  
  
 Приложение не должно использовать маркер инструкции после его освобождения; Диспетчер драйверов не проверяет допустимость маркера в вызове функции.  
  
## <a name="example"></a>Пример  
 Это хороший опыт программирования для бесплатных дескрипторов. Однако для простоты в следующем примере не включается код, освобождающий выделенные дескрипторы. Пример освобождения дескрипторов см. в разделе [функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
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
|Выделение маркера|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Закрытие курсора|[Функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Освобождение маркера|[Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Задание имени курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
