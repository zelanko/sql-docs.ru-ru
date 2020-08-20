---
description: Сводка по функциям ODBC
title: Сводка функций ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50a0b9146acd71f87b4dd65bbdd34c67725e9948
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487377"
---
# <a name="odbc-function-summary"></a>Сводка по функциям ODBC
В следующей таблице перечислены функции ODBC, сгруппированные по типам задач, а также указано обозначение соответствия и краткое описание назначения каждой функции. Дополнительные сведения о соотношении соответствия см. [в разделе ODBC и стандартную CLI](../../../odbc/reference/odbc-and-the-standard-cli.md). Дополнительные сведения о синтаксисе и семантике для каждой функции см. в [справочнике по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Приложение может вызвать функцию **SQLGetInfo** для получения сведений о согласованности драйвера. Чтобы получить сведения о поддержке определенной функции в драйвере, приложение может вызвать **SQLGetFunctions**.  
  
|Задача|Имя функции|Соответствия|Назначение|  
|----------|-------------------|-----------------|-------------|  
|Подключение к источнику данных|[Функцию SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Получает дескриптор среды, соединения, инструкции или дескриптора.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Подключается к определенному драйверу по имени источника данных, ИДЕНТИФИКАТОРу пользователя и паролю.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Подключается к определенному драйверу по строке подключения или запрашивает у пользователя диалоговые окна подключения диспетчера драйверов и драйвера.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Возвращает последовательные уровни атрибутов соединения и допустимые значения атрибутов. Если для каждого атрибута соединения указано значение, подключается к источнику данных.|  
|Получение сведений о драйвере и источнике данных|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Возвращает список доступных источников данных.<br /><br /> Возвращает список установленных драйверов и их атрибутов.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Возвращает сведения о конкретном драйвере и источнике данных.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Возвращает поддерживаемые функции драйвера.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Возвращает сведения о поддерживаемых типах данных.|  
|Установка и получение атрибутов драйвера|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Задает атрибут соединения.<br /><br /> Возвращает значение атрибута соединения.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Задает атрибут среды.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Возвращает значение атрибута среды.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Задает атрибут инструкции.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Возвращает значение атрибута инструкции.|  
|Установка и получение полей дескриптора|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Возвращает значение одного поля дескриптора.<br /><br /> Возвращает значения нескольких полей дескриптора.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Задает одно поле дескриптора.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Задает несколько полей дескриптора.|  
||[склкопидеск](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Копирует данные дескриптора из одного дескриптора дескриптора в другой.|  
|Подготовка запросов SQL|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Подготавливает инструкцию SQL для последующего выполнения.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Назначает хранилище для параметра в инструкции SQL.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Возвращает имя курсора, связанное с маркером инструкции.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Задает имя курсора.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Задает параметры, управляющие поведением курсора.|  
|Отправка запросов|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Выполняет подготовленную инструкцию.<br /><br /> Выполняет инструкцию.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Возвращает текст инструкции SQL, переведенный драйвером.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Возвращает описание указанного параметра в операторе.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Возвращает количество параметров в операторе.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Используется в сочетании с **SQLPutData** для предоставления данных параметров во время выполнения. (Полезно для длинных значений данных.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Отправляет часть или все значения данных для параметра. (Полезно для длинных значений данных.)|  
|Получение результатов и сведений о результатах|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Возвращает количество строк, затронутых запросом INSERT, UPDATE или DELETE.<br /><br /> Возвращает число столбцов в результирующем наборе.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Описывает столбец в результирующем наборе.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Описывает атрибуты столбца в результирующем наборе.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Назначает хранилище для столбца результатов и указывает тип данных.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Возвращает несколько результирующих строк.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Возвращает прокручиваемые строки результатов.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Возвращает часть или весь столбец одной строки результирующего набора. (Полезно для длинных значений данных.)|  
||[функция SQLSetPos;](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Размещает курсор в полученном блоке данных и позволяет приложению обновлять данные в наборе строк, а также обновлять или удалять данные в результирующем наборе.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Выполняет операции групповой вставки и операций с массовыми закладками, включая обновление, удаление и выборку по закладке.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Определяет, имеется ли больше результирующих наборов, и, если это так, инициализирует обработку для следующего результирующего набора.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Возвращает дополнительные диагностические сведения (одно поле структуры диагностических данных).|  
||[Функции SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Возвращает дополнительные диагностические сведения (несколько полей структуры диагностических данных).|  
|Получение сведений о системных таблицах источника данных (функции каталога)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Открыть группу|Возвращает список столбцов и связанные с ними привилегии для одной или нескольких таблиц.<br /><br /> Возвращает список имен столбцов в указанных таблицах.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Возвращает список имен столбцов, составляющих внешние ключи, если они существуют для указанной таблицы.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Возвращает список имен столбцов, из которых состоит первичный ключ таблицы.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Возвращает список входных и выходных параметров, а также столбцы, составляющие результирующий набор для указанных процедур.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Возвращает список имен процедур, хранящихся в указанном источнике данных.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Открыть группу|Возвращает сведения о оптимальном наборе столбцов, которые уникально идентифицируют строку в указанной таблице, или столбцы, которые автоматически обновляются, когда какое-либо значение в строке обновляется транзакцией.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Возвращает статистику по одной таблице и списку индексов, связанных с таблицей.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Возвращает список таблиц и привилегий, связанных с каждой таблицей.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Открыть группу|Возвращает список имен таблиц, хранящихся в указанном источнике данных.|  
|Завершение оператора|[Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Завершает обработку инструкции, отменяет ожидающие результаты и при необходимости освобождает все ресурсы, связанные с этим маркером инструкции.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Закрывает курсор, Открытый в маркере инструкции.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Отменяет обработку инструкции.|  
||[склканцелхандле](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Отменяет обработку инструкции или соединения.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Фиксирует или откатывает транзакцию.|  
|Завершение подключения|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Закрывает подключение.<br /><br /> Освобождает окружение, соединение, инструкцию или дескриптор.|
