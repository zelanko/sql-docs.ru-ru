---
title: Функция SQLNumParams | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNumParams
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNumParams
helpviewer_keywords:
- SQLNumParams function [ODBC]
ms.assetid: dbf2da44-253b-4094-bd6b-29bafc23c7a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72447e0aa7f913818b182c8996e3a269d034d43b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770304"
---
# <a name="sqlnumparams-function"></a>SQLNumParams, функция
**Соответствие стандартам**  
 Версия была введена: ODBC 1.0 соответствует стандартам: ISO-92  
  
 **Сводка**  
 **SQLNumParams** возвращает число параметров в инструкции SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLNumParams(  
     SQLHSTMT        StatementHandle,  
     SQLSMALLINT *   ParameterCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *ParameterCountPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено число параметров в инструкции.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLNumParams** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE может быть получен путем вызова **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLNumParams** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. **SQLNumParams** была вызвана функция, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* ; **SQLNumParams** функция затем вызывается снова для *StatementHandle*.<br /><br /> Или **SQLNumParams** была вызвана функция, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*  из другого потока в многопоточных приложениях.|  
|HY010|Ошибка последовательности функций|(DM), что функция была вызвана до вызова метода **SQLPrepare** или **SQLExecDirect** для *StatementHandle*.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLNumParams** была вызвана функция.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 **SQLNumParams** можно вызывать только после **SQLPrepare** был вызван.  
  
 Если инструкция, связанные с *StatementHandle* не содержит параметров, **SQLNumParams** задает **ParameterCountPtr* 0.  
  
 Число параметров, возвращенных **SQLNumParams** то же значение, что поле SQL_DESC_COUNT IPD.  
  
 Дополнительные сведения см. в разделе [описания параметров](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка буфер к параметру|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Возвращение сведений о параметре в операторе|[Функция SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
