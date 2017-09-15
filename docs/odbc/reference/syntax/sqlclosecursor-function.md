---
title: "Функция SQLCloseCursor | Документы Microsoft"
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
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0921de0c8bc117ca86f4aaabd273efff1f09a9e6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlclosecursor-function"></a>Функция SQLCloseCursor
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLCloseCursor** закрывает курсор, который был открыт в инструкции и отменяет ожидающие результаты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLCloseCursor** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL _HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLCloseCursor** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|24000|Недопустимое состояние курсора|Курсор не был открыт на *StatementHandle*. (Это значение возвращается только по ODBC 3. *x* драйвера.)|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в * \*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для * StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 **SQLCloseCursor** возвращает SQLSTATE 24000 (недопустимое состояние курсора), если никакой курсор открыт. Вызов **SQLCloseCursor** эквивалентно вызову **SQLFreeStmt** с параметром SQL_CLOSE, за исключением того, **SQLFreeStmt** с SQL_CLOSE не оказывает влияния на приложения, если курсор не открыт на инструкции, а **SQLCloseCursor** возвращает SQLSTATE 24000 (недопустимое состояние курсора).  
  
> [!NOTE]  
>  Если ODBC 3. *x* приложения, работа с ODBC 2.* x* драйвер вызывает **SQLCloseCursor** Если никакой курсор открыт, SQLSTATE 24000 (недопустимое состояние курсора) не возвращается, поскольку диспетчер драйверов сопоставляет **SQLCloseCursor** для **SQLFreeStmt** с SQL_CLOSE.  
  
 Дополнительные сведения см. в разделе [закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
## <a name="code-example"></a>Пример кода  
 В разделе [функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [SQLConnect, функция](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Освобождение дескриптора|[Функция SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Обработка нескольких результирующих наборов|[Функция SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
