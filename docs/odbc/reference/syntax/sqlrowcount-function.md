---
title: Функция SQLRowCount | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cbca03e7c3e381b803196a1bf7bb227ebeea03b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81293374"
---
# <a name="sqlrowcount-function"></a>Функция SQLRowCount
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLRowCount** возвращает количество строк, затронутых инструкцией **Update**, **INSERT**или **Delete** ; Операция SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK в **SQLBulkOperations**; или операция SQL_UPDATE или SQL_DELETE в **SQLSetPos**.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *RowCountPtr*  
 Проверки Указывает на буфер, в котором возвращается число строк. Для инструкций **Update**, **INSERT**и **Delete** для SQL_ADD, SQL_UPDATE_BY_BOOKMARK и SQL_DELETE_BY_BOOKMARK операций в **SQLBulkOperations**, а также для SQL_UPDATE или SQL_DELETE операций в режиме **SQLSetPos**значение, возвращаемое в **RowCountPtr* , — это либо количество строк, затронутых запросом, либо-1, если количество затронутых строк недоступно.  
  
 При вызове **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos или SQLMoreResults** в поле SQL_DIAG_ROW_COUNT структуры диагностических данных задается количество строк, а количество строк кэшируется в зависимости от реализации. **SQLRowCount** возвращает значение счетчика кэшированных строк. Значение счетчика кэшированных строк допустимо до тех пор, пока для маркера инструкции не будет установлено состояние "подготовлено" или "выделено", инструкция повторно выполняется или вызывается **SQLCloseCursor** . Обратите внимание, что если функция была вызвана с момента установки поля SQL_DIAG_ROW_COUNT, значение, возвращаемое функцией **SQLRowCount** , может отличаться от значения в поле SQL_DIAG_ROW_COUNT, так как поле SQL_DIAG_ROW_COUNT сбрасывается в значение 0 любым вызовом функции.  
  
 Для других инструкций и функций драйвер может определить значение, возвращаемое в \* *RowCountPtr*. Например, некоторые источники данных могут возвращать количество строк, возвращаемых инструкцией **SELECT** или функцией каталога, перед получением строк.  
  
> [!NOTE]  
>  Многие источники данных не могут возвращать количество строк в результирующем наборе перед их получением; для обеспечения максимальной совместимости приложения не должны полагаться на такое поведение.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLRowCount** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLRowCount** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции **SQLRowCount** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) функция была вызвана до вызова **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** для *статеменсандле*.<br /><br /> (DM) была вызвана асинхронно исполняемая функция для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Если последняя инструкция SQL, выполненная в обработчике инструкции, не является инструкцией **Update**, **INSERT**или **Delete** или если аргумент *операции* в предыдущем вызове **SQLBulkOperations** не был SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK или если аргумент *операции* в предыдущем вызове функции **SQLSetPos** не SQL_UPDATE или SQL_DELETE, то значение **RowCountPtr* определяется драйвером. Дополнительные сведения см. [в разделе Определение количества затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Исполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Исполнение подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
