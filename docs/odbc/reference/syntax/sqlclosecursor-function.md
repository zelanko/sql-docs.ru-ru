---
title: Функция SQLCloseCursor | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 912e4d109a9e769442c65d292ff190d79705eb21
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63252802"
---
# <a name="sqlclosecursor-function"></a>Функция SQLCloseCursor
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLCloseCursor** закрывает курсор, который был открыт в инструкции и отменяет ожидающие результаты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLCloseCursor** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE может быть получен путем вызова **SQLGetDiagRec** с *HandleType* из SQL _HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLCloseCursor** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|24000|Недопустимое состояние курсора|Отсутствует курсор был открыт на *StatementHandle*. (Это значение возвращается только с ODBC 3. *x* драйвера.)|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 **SQLCloseCursor** возвращает SQLSTATE 24000 (недопустимое состояние курсора), если курсор не открыт. Вызов **SQLCloseCursor** эквивалентно вызову **SQLFreeStmt** с параметром SQL_CLOSE, за исключением, **SQLFreeStmt** с SQL_CLOSE не оказывает влияния на приложения, если никакой курсор открыт на инструкции, то время как **SQLCloseCursor** возвращает SQLSTATE 24000 (недопустимое состояние курсора).  
  
> [!NOTE]  
>  Если ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер вызывает **SQLCloseCursor** когда никакой курсор открыт, SQLSTATE 24000 (недопустимое состояние курсора) не выводятся, поскольку диспетчер драйверов сопоставляет **SQLCloseCursor** для **SQLFreeStmt** с SQL_CLOSE.  
  
 Дополнительные сведения см. в разделе [закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
## <a name="code-example"></a>Пример кода  
 См. в разделе [функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Освобождение дескриптора|[Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Обработка нескольких результирующих наборов|[Функция SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
