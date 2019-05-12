---
title: Функция SQLRowCount | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ccc858603fc5662f380c5d3ae48d777005ddac4
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537153"
---
# <a name="sqlrowcount-function"></a>Функция SQLRowCount
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLRowCount** возвращает количество строк, затронутых **обновление**, **вставить**, или **удалить** оператор; SQL_ADD SQL_UPDATE_BY_BOOKMARK или SQL_ Операция DELETE_BY_BOOKMARK **SQLBulkOperations**; или выполнении операций SQL_UPDATE и SQL_DELETE **SQLSetPos**.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *RowCountPtr*  
 [Выход] Указывает на буфер, в которую будет возвращено количество строк. Для **обновление**, **вставить**, и **удалить** инструкций для операций в SQL_ADD SQL_UPDATE_BY_BOOKMARK и SQL_DELETE_BY_BOOKMARK  **SQLBulkOperations**и для операций в SQL_UPDATE или SQL_DELETE **SQLSetPos**, значение, возвращаемое в **RowCountPtr* — либо количество строк, затронутых запрос или -1, если количество затронутых строк не доступен.  
  
 Когда **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos или SQLMoreResults** называется SQL_DIAG_ROW_COUNT поля структуры диагностических данных задается количество строк и число строк кэшируется образом зависит от реализации. **SQLRowCount** возвращает значение счетчика кэшированной строке. Значение счетчика кэшированной строке является допустимым, пока не будет снова установить значение подготовленного или выделенное состояние дескриптора инструкции, инструкция будет выполнена повторно, или **SQLCloseCursor** вызывается. Обратите внимание, что если функция была вызвана, поскольку поле SQL_DIAG_ROW_COUNT была задана, значение, возвращаемое функцией **SQLRowCount** может отличаться от значения в поле SQL_DIAG_ROW_COUNT, так как поле SQL_DIAG_ROW_COUNT сбрасывается до 0 по вызову функции.  
  
 Для других инструкций и функций, драйвер может определить значение, возвращаемое в \* *RowCountPtr*. Например, некоторые источники данных может иметь возможность возвращать количество строк, возвращенных **ВЫБЕРИТЕ** инструкции или функции каталога перед извлечением строк.  
  
> [!NOTE]  
>  Многие источники данных не может возвращать количество строк в результирующем наборе перед извлечением. для максимальной совместимости приложений не следует полагаться на это поведение.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLRowCount** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLRowCount** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLRowCount** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM), что функция была вызвана до вызова метода **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** для  *StatementHandle*.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Если последней инструкцией SQL, выполненной для дескриптора инструкции не **обновление**, **вставить**, или **удалить** инструкции или, если *операции* аргумент в предыдущем вызове **SQLBulkOperations** не SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK, или если *операции* аргумента в предыдущем вызове  **SQLSetPos** не SQL_UPDATE или SQL_DELETE, значение **RowCountPtr* является, определяемым драйвером. Дополнительные сведения см. в разделе [определение число затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнении подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
