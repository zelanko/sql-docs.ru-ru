---
title: Резюме функции ODBC (ru) Документы Майкрософт
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
ms.openlocfilehash: c10cc7880cf941a1490f963e21e8b44bc91db215
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298925"
---
# <a name="odbc-function-summary"></a>Сводка по функциям ODBC
В следующей таблице перечислены функции ODBC, сгруппированные по типу задачи, и включает обозначение соответствия и краткое описание цели каждой функции. Для получения дополнительной информации о обозначениях соответствия, [см.](../../../odbc/reference/odbc-and-the-standard-cli.md) Для получения дополнительной информации о синтаксисе [ODBC API Reference](../../../odbc/reference/syntax/odbc-api-reference.md)и семантике для каждой функции см.  
  
 Приложение может позвонить в функцию **S'LGetInfo** для получения информации о соответствии драйвера. Для получения информации о поддержке определенной функции в драйвере приложение может вызвать **S'LGetFunctions.**  
  
|Задача|Имя функции|Соответствия|Цель|  
|----------|-------------------|-----------------|-------------|  
|Подключение к источнику данных|[СЗЛАллокХэндл](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Получает ручку среды, соединения, оператора или дескриптора.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Подключается к конкретному драйверу по имени источника данных, идентификатору пользователя и паролю.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Подключается к конкретному драйверу по строке подключения или запрашивает, чтобы диспетчер драйвера и драйвер отображали диалоговые ящики соединения для пользователя.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Возвращает последовательные уровни атрибутов соединения и допустимые значения атрибутов. Когда значение было определено для каждого атрибута соединения, подключается к источнику данных.|  
|Получение информации о драйвере и источнике данных|[Источники данных S'LData](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Возвращает список доступных источников данных.<br /><br /> Возвращает список установленных драйверов и их атрибуты.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Возвращает информацию о конкретном драйвере и источнике данных.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Возвращает поддерживаемые функции драйвера.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Возвращает информацию о поддерживаемых типах данных.|  
|Настройка и извлечение атрибутов драйвера|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Устанавливает атрибут соединения.<br /><br /> Возвращает значение атрибута соединения.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Устанавливает атрибут среды.|  
||[СЗЛГетЕнвТтр](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Возвращает значение атрибута среды.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Устанавливает атрибут оператора.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Возвращает значение атрибута оператора.|  
|Настройка и извлечения полей дескриптора|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Возвращает значение одного поля дескриптора.<br /><br /> Возвращает значения нескольких полей дескриптора.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Устанавливает одно поле дескриптора.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Устанавливает несколько полей дескриптора.|  
||[СЗЛКопиДеск](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Копирует информацию о дескриптора с одной дескрипторной ручки на другую.|  
|Подготовка запросов на СЗЛ|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Подготовьте выписку по S'L для последующего выполнения.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Назначает хранилище для параметра в выписке s'L.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Возвращает имя курсора, связанное с ручкой оператора.|  
||[СЗЛСетКурсОрНамейм](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Упогоняет имя курсора.|  
||[СЗЛСЕтПрокрутисОпции](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Устанавливает параметры, которые контролируют поведение курсора.|  
|Отправка запросов|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Выполняет подготовленную инструкцию.<br /><br /> Выполняет инструкцию.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Возвращает текст заявления S'L в переводе водителя.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Возвращает описание для определенного параметра в заявлении.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Возвращает количество параметров в отчете.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Используется в сочетании с **S'LPutData** для предоставления данных параметров во время выполнения. (Полезно для длинных значений данных.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Отправляет часть или все значение данных для параметра. (Полезно для длинных значений данных.)|  
|Получение результатов и информации о результатах|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Возвращает количество строк, затронутых запросом на вставку, обновление или удаление.<br /><br /> Возвращает число столбцов в результирующем наборе.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Описывает столбец в наборе результатов.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Описывает атрибуты столбца в наборе результатов.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Назначает хранилище для результата столбца и определяет тип данных.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Возвращает несколько строк результатов.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Возвращает прокрутки строк и результатов.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Возвращает часть или все из одного столбца одного ряда набора результатов. (Полезно для длинных значений данных.)|  
||[функция SQLSetPos;](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Позиционирует курсор в извлеченном блоке данных и позволяет приложению обновлять данные в строке или обновлять или удалять данные в наборе результатов.|  
||[СЗЛБалКОперации](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Выполняет объемные вставки и объемные операции закладок, включая обновление, удаление и получение закладкой.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Определяет, доступно ли больше наборов результатов, и если да, то инициализирует обработку для следующего набора результатов.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Возвращает дополнительную диагностическую информацию (единое поле структуры диагностических данных).|  
||[Функции SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Возвращает дополнительную диагностическую информацию (несколько полей структуры диагностических данных).|  
|Получение информации о системных таблицах источника данных (функции каталога)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Открытая группа|Возвращает список столбцов и связанных с ними привилегий для одной или нескольких таблиц.<br /><br /> Возвращает список имен столбцов в указанные таблицы.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Возвращает список имен столбцов, которые составляют иностранные ключи, если они существуют для указанной таблицы.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Возвращает список имен столбцов, которые составляют основной ключ для таблицы.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Возвращает список входных и выходных параметров, а также столбцов, которые составляют результат, установленный для указанных процедур.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Возвращает список имен процедур, хранящихся в определенном источнике данных.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Открытая группа|Возвращает информацию об оптимальном наборе столбцов, которые однозначно идентифицируют строку в указанной таблице, или столбцы, которые автоматически обновляются при обновлении значения строки транзакцией.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Возвращает статистику о одной таблице и списке индексов, связанных с таблицей.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Возвращает список таблиц и привилегий, связанных с каждой таблицей.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Открытая группа|Возвращает список имен таблиц, хранящихся в определенном источнике данных.|  
|Прекращение заявления|[Функция SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Завершает обработку оператора, отбрасывает ожидающие результатов и, по желанию, освобождает все ресурсы, связанные с обработкой оператора.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Закрывает курсор, который был открыт на ручке оператора.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Отменяет обработку оператора.|  
||[СЗЛКанскхельн](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Отменяет обработку оператора или соединения.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Коммитс или откат транзакции.|  
|Прекращение соединения|[СЗЛДИСКоннект](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Закрывает подключение.<br /><br /> Выпускает ручку среды, соединения, оператора или дескриптора.|
