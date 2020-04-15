---
title: Функция S'LFreeStmt Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e252769c26a5491100094b1243b9c2c6bb67d94d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285704"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt, функция
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **SLFreeStmt** прекращает обработку, связанную с конкретным заявлением, закрывает все открытые курсоры, связанные с выпиской, отбрасывает ожидающие результатов или, по желанию, высвобождает все ресурсы, связанные с обработкой оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора  
  
 *Параметр*  
 (Вход) Один из следующих вариантов:  
  
 SQL_ CLOSE: Закрывает курсор, связанный с *StatementHandle* (если он был определен) и отбрасывает все ожидающие результаты. Приложение может повторно открыть этот курсор позже, выполнив выписку **SELECT** снова с теми же или различными значениями параметров. Если курсор не открыт, эта опция не имеет эффекта для приложения. **Кроме** того, для закрытия курсора можно позвонить курсору. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/closing-the-cursor.md)  
  
 SQL_DROP: Этот вариант является амортизированным. Звонок на **S'LFreeStmt** с *опцией* SQL_DROP отображается в менеджере драйверов в [S'LFreeHandle.](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
 SQL_UNBIND: Устанавливает SQL_DESC_COUNT поле ARD до 0, высвобождая все буферы столбцов, связанные **s'LBindCol** для данного *StatementHandle*. Это не развязывает столбец закладки; для этого SQL_DESC_DATA_PTR поле ARD для колонки закладок установлен на NULL. Обратите внимание, что если эта операция выполняется на явно выделенном дескрипторе, который используется более чем одним оператором, операция повлияет на привязки всех инструкций, которые разделяют дескриптор. Для получения дополнительной информации смотрите [Обзор получения результатов (Основные)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Устанавливает SQL_DESC_COUNT поле APD до 0, высвобождая все параметры, установленные **S'LBindParameter** для данного *StatementHandle.* Если эта операция выполняется на явно выделенном дескрипторе, который используется более чем одним оператором, эта операция повлияет на привязки всех инструкций, которые разделяют дескриптор. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LFreeStmt** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанную с этим стоимость S'LSTATE можно получить, позвонив по **телефону s'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_STMT и *ручки* *statementHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LFreeStmt,** и приведены в изъяны каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась, когда был вызван **S'LFreeStmt.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана набором *опционов* для SQL_RESET_PARAMS до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Асинхронно выполнение функции был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY092|Тип опции вне диапазона|(DM) Значение, указанное для аргумента *Вариант* не было:<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов **S'LFreeStmt** с SQL_CLOSE опцией эквивалентен вызову **S'LCloseCursor,** за исключением того, что **S'LFreeStmt** с SQL_CLOSE не влияет на приложение, если в заявлении нет курсора. Если курсор не открыт, вызов в **S'LCloseCursor** возвращает S'LSTATE 24000 (недействительное состояние курсора).  
  
 Приложение не должно использовать ручку оператора после его освобождения; Менеджер драйвера не проверяет достоверность ручки в вызове функции.  
  
## <a name="example"></a>Пример  
 Это хорошая практика программирования для свободных ручек. Однако для простоты следующий пример не включает код, освобождая выделенные ручки. Например, как можно бесплатно осваить ручки, [см.](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
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
|Выделение ручки|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Закрытие курсора|[Функция SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Освобождение ручки|[SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Установка имени курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
