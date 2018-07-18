---
title: Функция SQLRowCount | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9ad642032c2bee346381bd74a2dc5db46bb3d0f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32920179"
---
# <a name="sqlrowcount-function"></a>Функция SQLRowCount
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLRowCount** возвращает число строк, затронутых **обновление**, **вставить**, или **удалить** оператора, SQL_ADD SQL_UPDATE_BY_BOOKMARK или SQL_ Операция DELETE_BY_BOOKMARK **SQLBulkOperations**; или выполнении операций SQL_UPDATE и SQL_DELETE **SQLSetPos**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *RowCountPtr*  
 [Выход] Указывает на буфер, в который возвращается число строк. Для **обновление**, **вставить**, и **удаление** инструкции для каждой операции SQL_ADD SQL_UPDATE_BY_BOOKMARK и SQL_DELETE_BY_BOOKMARK в  **SQLBulkOperations**и для операций в SQL_UPDATE или SQL_DELETE **SQLSetPos**, значение, возвращаемое в **RowCountPtr* либо число строк, затронутых запрос или – 1, если количество затронутых строк не доступен.  
  
 Когда **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos или SQLMoreResults** вызывается SQL_DIAG_ROW_COUNT поля структуры диагностики данных установлено значение количества строк и количество строк кэшируется в виде зависят от реализации. **SQLRowCount** возвращает значение кэшированных строки. Значение строки кэшированных является допустимым, пока не будет снова установить значение состояния подготовленных или выделенного дескриптора инструкции, инструкция reexecuted, или **SQLCloseCursor** вызывается. Обратите внимание, что если функция была вызвана, поскольку была задана SQL_DIAG_ROW_COUNT поле, значение, возвращаемое **SQLRowCount** может отличаться от значения в поле SQL_DIAG_ROW_COUNT, так как поле SQL_DIAG_ROW_COUNT сбрасывается до 0 по вызову функции.  
  
 Для других инструкций и функций, драйвер может определить значение, возвращаемое в \* *RowCountPtr*. Например, некоторые источники данных можно возвращать количество строк, возвращенных **ВЫБЕРИТЕ** оператора или функции каталога перед выборкой строк.  
  
> [!NOTE]  
>  Многие источники данных не может возвращать количество строк в результирующем наборе перед выборкой их; для максимальной совместимости приложений не следует полагаться на это поведение.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLRowCount** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLRowCount** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLRowCount** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM), функция был вызван до вызова метода **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** для  *StatementHandle*.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 При выполнении последней инструкции SQL для дескриптора инструкции не **обновление**, **вставить**, или **удалить** оператор или, если *операции* аргумент в предыдущем вызове **SQLBulkOperations** не SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK, или если *операции* аргумента в предыдущем вызове  **SQLSetPos** не SQL_UPDATE или SQL_DELETE значение **RowCountPtr* является определяемым драйвером. Дополнительные сведения см. в разделе [определение число затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнения подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
