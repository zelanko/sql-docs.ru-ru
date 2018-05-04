---
title: Сводка по функциям ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74352c77e64a07b3c41bae784560b946ea620ebb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-function-summary"></a>Сводка по функциям ODBC
В следующей таблице перечислены функции ODBC, сгруппированные по типу задачи и включает обозначение соответствия и краткое описание назначения каждой функции. Дополнительные сведения о совместимости назначения в разделе [ODBC и стандартная CLI](../../../odbc/reference/odbc-and-the-standard-cli.md). Дополнительные сведения о синтаксисе и семантику для каждой функции см. в разделе [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Приложение может вызвать **SQLGetInfo** функции для получения соответствия сведений о драйвере. Чтобы получить сведения о поддержке определенную функцию в драйвере, приложение может вызвать **SQLGetFunctions**.  
  
|Задача|Имя функции|Соответствия|Назначение|  
|----------|-------------------|-----------------|-------------|  
|Подключение к источнику данных|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO-92|Получает дескриптор среды, соединения, оператор или дескриптора.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO-92|Подключается к конкретный драйвер, имя источника данных, идентификатор пользователя и пароль.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|интерфейс ODBC|Подключается к конкретный драйвер, строку подключения или запросы, что диспетчер драйверов и драйвер отображать диалоговые окна подключения для пользователя.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|интерфейс ODBC|Возвращает последовательные уровни атрибуты соединения и допустимые значения атрибута. Если указано значение для каждого атрибута соединения, подключается к источнику данных.|  
|Получение сведений о драйвера и источника данных|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO-92<br /><br /> интерфейс ODBC|Возвращает список доступных источников данных.<br /><br /> Возвращает список установленных драйверов и их атрибуты.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO-92|Возвращает сведения о конкретных драйверов и источник данных.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO-92|Возвращает поддерживаемые функции драйвера.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO-92|Возвращает сведения о поддерживаемых типах данных.|  
|Установка и получение атрибутов драйвера|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO-92<br /><br /> ISO-92|Задает атрибут соединения.<br /><br /> Возвращает значение атрибута соединения.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO-92|Задает атрибут среды.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO-92|Возвращает значение атрибута среды.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO-92|Задает атрибут инструкции.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO-92|Возвращает значение атрибута инструкции.|  
|Установка и получение поля дескриптора|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO-92<br /><br /> ISO-92|Возвращает значение поля одного дескриптора.<br /><br /> Возвращает значения нескольких полей дескриптора.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO-92|Задает поле одного дескриптора.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO-92|Задает несколько поля дескриптора.|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO-92|Копирует данные дескриптора с одного дескриптора на другой.|  
|Подготовка SQL запросов|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO-92|Подготавливает инструкцию SQL для выполнения в будущем.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|интерфейс ODBC|Назначает хранения в качестве параметра в инструкции SQL.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO-92|Возвращает имя курсора, связанной с дескриптором инструкции.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO-92|Указывает имя курсора.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|интерфейс ODBC|Задает параметры, которые управляют поведением курсора.|  
|Отправка запросов|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO-92<br /><br /> ISO-92|Выполняет подготовленную инструкцию.<br /><br /> Выполняет инструкцию.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|интерфейс ODBC|Возвращает текст инструкции SQL, которые преобразуются с помощью драйвера.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|интерфейс ODBC|Возвращает описание для определенного параметра в инструкции.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO-92|Возвращает число параметров в инструкции.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO-92|Использовать в сочетании с **SQLPutData** для предоставления данных параметра во время выполнения. (Это удобно для длинных данных значений.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO-92|Отправляет части или всех значений данных для параметра. (Это удобно для длинных данных значений.)|  
|Получение результатов и сведения о результатах|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO-92<br /><br /> ISO-92|Возвращает количество строк, затронутых инструкцией insert, update или delete запроса.<br /><br /> Возвращает число столбцов в результирующем наборе.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO-92|Описывает столбец в результирующем наборе.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO-92|Описывает атрибуты столбцов в результирующем наборе.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO-92|Назначает хранилища для столбца результатов и указывает тип данных.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO-92|Возвращает несколько строк результата.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO-92|Возвращает прокручиваемые результирующие строки.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO-92|Возвращает часть или все из одного столбца из одной строки результата задать. (Это удобно для длинных данных значений.)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|интерфейс ODBC|Позиционирует курсор в пределах блока извлеченных данных и позволяет приложению обновлять данные в наборе строк, или для обновления или удаления данных в результирующем наборе.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|интерфейс ODBC|Выполняет операции массовой вставки и закладки массовой операции, включая обновления, удаления и выборку по закладке.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|интерфейс ODBC|Определяет, есть ли дополнительные результирующие наборы доступных и если да, инициализирует обработку следующего набора результатов.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO-92|Возвращает дополнительную диагностическую информацию (одним полем структуры диагностики данных).|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO-92|Возвращает дополнительную диагностическую информацию (несколько полей структуры диагностики данных).|  
|Получение сведений о системных таблицах источника данных (функции работы с каталогами)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|интерфейс ODBC<br /><br /> Open Group|Возвращает список столбцов и привилегий для одной или нескольких таблиц.<br /><br /> Возвращает список имен столбцов в указанных таблицах.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|интерфейс ODBC|Возвращает список имен столбцов, составляющих внешние ключи, если они существуют, для указанной таблицы.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|интерфейс ODBC|Возвращает список имен столбцов, которые составляют первичный ключ для таблицы.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|интерфейс ODBC|Возвращает список входных данных и выходных параметров, а также столбцы, которые составляют результирующий набор для указанной процедуры.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|интерфейс ODBC|Возвращает список имен процедур, хранящихся в конкретного источника данных.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Open Group|Возвращает сведения о оптимальный набор столбцов, которые однозначно определяют строку в указанной таблицы или столбцы, которые автоматически обновляются, когда любое значение в строке обновляется транзакцией.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO-92|Возвращает статистику об одной таблицы и список индексов, связанных с таблицей.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|интерфейс ODBC|Возвращает список таблиц и права, связанные с каждой таблицей.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Open Group|Возвращает список имен таблиц, хранимых в конкретного источника данных.|  
|Завершение инструкции|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO-92|Завершает обработку инструкций, отменяет ожидающие результаты и, при необходимости освобождает все ресурсы, связанные с дескриптором инструкции.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO-92|Закрывает курсор, который был открыт дескриптор инструкции.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO-92|Отменяет обработку на инструкции.|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|интерфейс ODBC|Отменяет обработку на инструкции или соединения.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO-92|Фиксирует или откатывает транзакцию.|  
|Завершение подключения|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO-92<br /><br /> ISO-92|Закрывает соединение.<br /><br /> Освобождает дескриптор среды, соединения, оператор или дескриптора.|
