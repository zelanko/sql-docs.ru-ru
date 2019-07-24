---
title: Функция SQLCloseCursor | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef336a4deb734c0e44f9c15ae7f9faf0dcb32d93
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343153"
---
# <a name="sqlclosecursor-function"></a>Функция SQLCloseCursor
**Соответствия**  
 Представленная версия: Соответствие стандартам ODBC 3,0: ISO 92  
  
 **Сводка**  
 **SQLCloseCursor** закрывает курсор, который был открыт в инструкции, и отменяет ожидающие результаты.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLCloseCursor** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и маркером  *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLCloseCursor** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|24000|Недопустимое состояние курсора|В *статеменсандле*курсора не открыт. (Возвращается только ODBC 3. драйвер *x* .)|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией  *\** **SQLGetDiagRec** в буфере MessageText, описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) была вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле* , и он все еще выполнялся при вызове этой функции.<br /><br /> (DM) была вызвана асинхронно исполняемая функция для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращенного SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 **SQLCloseCursor** ВОЗВРАЩАЕТ значение SQLSTATE 24000 (недопустимое состояние курсора), если курсор не открыт. Вызов **SQLCloseCursor** эквивалентен вызову **SQLFreeStmt** с параметром SQL_CLOSE, за исключением того, что **SQLFreeStmt** с SQL_CLOSE не влияет на приложение, если курсор не открыт в инструкции, а  **SQLCloseCursor** возвращает значение SQLSTATE 24000 (недопустимое состояние курсора).  
  
> [!NOTE]  
>  Если ODBC 3. Приложение *x* , работающее с ODBC 2. драйвер *x* вызывает **SQLCloseCursor** , если курсор не открыт, значение SQLSTATE 24000 (недопустимое состояние курсора) не возвращается, так как диспетчер драйверов сопоставляет **SQLCloseCursor** с **SQLFreeStmt** с SQL_CLOSE.  
  
 Дополнительные сведения см. [в разделе заключение курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
## <a name="code-example"></a>Пример кода  
 См. раздел [функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Освобождение маркера|[Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Обработка нескольких результирующих наборов|[Функция SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
