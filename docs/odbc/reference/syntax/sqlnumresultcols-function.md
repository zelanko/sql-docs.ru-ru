---
title: Функция SQLNumResultCols | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNumResultCols
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLNumResultCols
helpviewer_keywords:
- SQLNumResultCols function [ODBC]
ms.assetid: d863179f-12a9-4b55-ac6b-7d84202d3da3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43c7f72869cf46fa12f942a3d31399cf3e316520
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68343545"
---
# <a name="sqlnumresultcols-function"></a>SQLNumResultCols, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLNumResultCols** возвращает количество столбцов в результирующем наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLNumResultCols(  
     SQLHSTMT        StatementHandle,  
     SQLSMALLINT *   ColumnCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *колумнкаунтптр*  
 Проверки Указатель на буфер, в котором возвращается число столбцов в результирующем наборе. Это число не включает в себя связанный столбец закладки.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLNumResultCols** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLNumResultCols** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*; Затем функция снова вызывалась в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции **склнумресултсколс** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) функция была вызвана до вызова **SQLPrepare** или **SQLExecDirect** для *статеменсандле*.<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.<br /><br /> Дополнительные сведения о том, когда можно освободить маркер инструкции, см. в разделе [функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md) .|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
 **SQLNumResultCols** может возвращать любое значение SQLSTATE, которое может быть возвращено **SQLPrepare** или **SQLExecute** при вызове после **SQLPrepare** и до **SQLExecute**, в зависимости от того, когда источник данных оценивает инструкцию SQL, связанную с инструкцией.  
  
## <a name="comments"></a>Комментарии  
 **SQLNumResultCols** может быть вызвана успешно только в том случае, если инструкция находится в состоянии preparedd, executeed или позиционировано.  
  
 Если инструкция, связанная с *статеменсандле* , не возвращает столбцы, **SQLNumResultCols** устанавливает для **колумнкаунтптр* значение 0.  
  
 Число столбцов, возвращаемых функцией **SQLNumResultCols** , совпадает со значением поля SQL_DESC_COUNT в IRD.  
  
 Дополнительные сведения см. [в разделе был создан результирующий набор?](../../../odbc/reference/develop-app/was-a-result-set-created.md) и [как используются метаданные](../../../odbc/reference/develop-app/how-is-metadata-used.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Привязка буфера к столбцу в результирующем наборе|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возврат сведений о столбце в результирующем наборе|[Функция SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Возврат сведений о столбце в результирующем наборе|[SQLDescribeCol, функция](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Исполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Исполнение подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Выборка блока данных или прокрутка результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка одной строки или блока данных в прямом направлении|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Выборка части или всего столбца данных|[Функция SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Подготовка инструкции SQL к выполнению|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Задание параметров прокрутки курсора|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
