---
title: "Функция SQLDisconnect | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDisconnect
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDisconnect
helpviewer_keywords: SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
caps.latest.revision: "31"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d210614a32c2dd8190c37777d3ac06a99756156
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqldisconnect-function"></a>Функция SQLDisconnect
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLDisconnect** закрывает соединение, связанное с этим дескриптором подключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConnectionHandle*  
 [Вход] Дескриптор соединения.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE или SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDisconnect** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DBC и *обработки* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLDisconnect** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01002|Отключить ошибки|Произошла ошибка во время отключения. Однако отключение успешно. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08003|Соединение не открыто|Соединение (DM), указанный в аргументе *ConnectionHandle* не был открыт.|  
|25000|Недопустимое состояние транзакции|Произошла транзакции в процессе на соединение, указанное в аргументе *ConnectionHandle*. Транзакция остается активной.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *ConnectionHandle*. Функция была вызвана, и перед его выполнением завершил [функция SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) был вызван для *ConnectionHandle*. Затем функция была вызвана снова на *ConnectionHandle*.<br /><br /> Функция был вызван, и до завершения выполнения **SQLCancelHandle** был вызван для *ConnectionHandle* из другого потока в многопоточных приложениях.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для *StatementHandle* связанных с *ConnectionHandle* и еще выполнялась при **SQLDisconnect** был вызывается.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *ConnectionHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для *StatementHandle*  связанных с *ConnectionHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Перед ответил на запрос источника данных, а соединение еще активен, истечения времени ожидания соединения. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *ConnectionHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 Если приложение вызывает **SQLDisconnect** после **SQLBrowseConnect** возвращает SQL_NEED_DATA и перед возвращением другого кода возврата, драйвер отменяет процесс просмотра соединение и возвращает соединение в несвязанной состояние.  
  
 Если приложение вызывает **SQLDisconnect** при незавершенной транзакции, связанной с дескриптором соединения драйвер возвращает SQLSTATE 25000 (недопустимое состояние транзакции), указывает, что транзакции без изменений и при открытом соединении. Незавершенная транзакция является запрос, который не зафиксирована или откатана с **SQLEndTran**.  
  
 Если приложение вызывает **SQLDisconnect** до освобождения всех инструкций, связанный с подключением драйвер, после успешного отключения из источника данных, освобождает этих инструкций и все дескрипторы, которые были явно выделенные при соединении. Тем не менее, если один или несколько инструкций, связанный с соединением по-прежнему выполняются асинхронно, **SQLDisconnect** возвращает значение SQL_ERROR со значением SQLSTATE HY010 (функция ошибка последовательности). Кроме того **SQLDisconnect** , чтобы освободить все связанные инструкции и все дескрипторы, явно назначенные в соединении, если соединение находится в приостановленном состоянии или **SQLDisconnect** был успешно отменена **SQLCancelHandle**.  
  
 Сведения о том, как приложение использует **SQLDisconnect**, в разделе [отключение от источника данных или драйвер](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="disconnecting-from-a-pooled-connection"></a>Отключение от подключения из пула подключений  
 Если включен пул соединений для совместно используемой среде, и приложение вызывает **SQLDisconnect** для подключения в этой среде, соединение возвращается в пул подключений и по-прежнему доступен для других компонентов, с помощью одной общей среде.  
  
## <a name="code-example"></a>Пример кода  
 В разделе [образца программы ODBC](../../../odbc/reference/sample-odbc-program.md), [функция SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), и [SQLConnect, функция](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выделение дескриптора|[Функция SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Подключение к источнику данных|[Функция SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Соединение с источником данных, используется поле строки или диалоговое окно соединения|[Функция SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Выполнение операции фиксации или отката|[Функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|Освобождение дескриптора соединения|[Функция SQLFreeConnect](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
