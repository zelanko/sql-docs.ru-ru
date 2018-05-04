---
title: Приложение а. коды ошибок ODBC | Документы Microsoft
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
- error codes [ODBC]
- SQLSTATE [ODBC]
- error codes [ODBC], SQLSTATE
ms.assetid: c06902e4-721d-42e2-b818-05f0e18e4ce0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23b6cc6a2c70db6265024cf270d0df165bc3c34d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="appendix-a-odbc-error-codes"></a>Приложение а. коды ошибок ODBC
В этом разделе рассматриваются значениях SQLSTATE для ODBC 3. *x*. Дополнительные сведения о ODBC 3. *x* значения SQLSTATE. в разделе [сопоставления SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md).  
  
 **SQLGetDiagRec** или **SQLGetDiagField** возвращает значения SQLSTATE, в соответствии с определением Open Group *управление данными: язык SQL (Structured Query), версия 2* (марта 1995 г.). Значения SQLSTATE являются строками, содержащими пять символов. В следующей таблице перечислены значения SQLSTATE, которые можно возвратить драйвер **SQLGetDiagRec**.  
  
 Строковое значение возвращается для SQLSTATE состоит из значения класса двух знаков, за которым следует значение подкласса трех символов. Значение класса «01» указывает на предупреждение и сопровождается код возврата SQL_SUCCESS_WITH_INFO. Класс значения, отличные от «01», за исключением класса «Обмена мгновенными Сообщениями», является ошибкой и могут быть загружены возвращаемое значение SQL_ERROR. Класс «Обмена мгновенными Сообщениями» относится к предупреждений и ошибок, которые являются производными от реализации ODBC. Подкласс значение «000» в любом классе указывает не подкласса для этой SQLSTATE. Назначение значений класса и подкласс определяется SQL-92.  
  
> [!NOTE]  
>  Несмотря на то, что возвращаемое значение SQL_SUCCESS, обычно указывается успешное выполнение функции, SQLSTATE 00000 также указывает на успешное завершение.  
  
|SQLSTATE|Ошибка|Могут быть возвращены из|  
|--------------|-----------|--------------------------|  
|01000|Общее предупреждение|Все функции ODBC, за исключением:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|01001|Конфликт операции с курсором|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01002|Отключить ошибки|**SQLDisconnect**|  
|01003|Функция set не поддерживает значение NULL|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|Строковые данные, усечение справа|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNative**<br /><br /> **SQL SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetCursorName**|  
|01006|Привилегия не отменена|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|Не предоставлено право доступа|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|Недопустимый атрибут строки соединения|**SQLBrowseConnect**<br /><br /> **SQLDriverConnec**|  
|01S01|Ошибка в строке|**SQLBulkOperations**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLSetPos**|  
|01S02|Значение параметра изменено|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01S06|Попытка выборки до появления результирующий набор возвращается первый набор строк|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|01S07|Частичное усечение|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01S08|Ошибка при сохранении файлового DSN|**SQLDriverConnect**|  
|01S09|Недопустимое ключевое слово|**SQLDriverConnect**|  
|07001|Неверное число параметров|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|Неправильное поле COUNT|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|Не подготовленной инструкции *курсором*|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|Нарушение атрибута ограниченного типа данных|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|07009|Недопустимый индекс дескриптора|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRecSQLSetPos**|  
|07S01|Недопустимое использование параметра по умолчанию|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|Клиенту не удается установить соединение|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|Имя подключения используется|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|Соединение не открыто|**SQLAllocHandle**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|Сервер отклонил соединение|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|Сбой подключения во время транзакции.|**SQLEndTran**|  
|08S01|Сбой связи|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21S01|Список вставляемых значений не соответствует списку столбцов|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21S02|Структура полученной таблицы не соответствуют списку столбцов|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|22001|Строковые данные, усечение справа|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetPos**|  
|22002|Индикатор обязательным, но не указано|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|Численное значение вне допустимого диапазона|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22007|Формат недопустимые даты и времени|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22008|Переполнение поля DateTime|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **QLParamData**<br /><br /> **SQLPutData**|  
|22012|Деление на ноль|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|Переполнение поля интервала|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22018|Недопустимое символьное значение для спецификации приведения|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22019|Недопустимый escape-символ|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|Недопустимая escape-последовательность|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|Строковые данные, несовпадение длины|**SQLParamData**|  
|23000|Нарушение ограничения целостности|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|24000|Недопустимое состояние курсора|**SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|Недопустимое состояние транзакции|**SQLDisconnect**|  
|25S01|Состояние транзакции|**SQLEndTran**|  
|25S02|Транзакция все еще активна|**SQLEndTran**|  
|25S03|Откат транзакции|**SQLEndTran**|  
|28000|Недопустимая спецификация авторизации|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|Недопустимое имя курсора|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetCursorName**|  
|3C000|Повторяющееся имя курсора|**SQLSetCursorName**|  
|3D000|Недопустимое имя каталога|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F000|Недействительное имя схемы|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|Сбой сериализации|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|Нарушение ограничения целостности|**SQLEndTran**|  
|40003|Неизвестный завершение операторов|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|Синтаксическая ошибка или нарушение доступа|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|42S01|Базовая таблица или представление уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S02|Базовая таблица или представление не найдены|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S11|Индекс уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S12|Индекс не найден|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S21|Столбец уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S22|Столбец не найден|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|Нарушение параметра WITH CHECK OPTION|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY000|Общая ошибка|Все функции ODBC, за исключением:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY001|Ошибка выделения памяти|Все функции ODBC, за исключением:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY003 И СООБЩЕНИЕМ|Недопустимый тип буфера приложения|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|Недопустимый тип данных SQL|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|Нужная инструкция не подготовлена|**SQLCopyDesc**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008|Операция отменена|Все функции ODBC, которые могут обрабатываться асинхронно:<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|Недопустимое использование пустого указателя|**SQLAllocHandle**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|Ошибка последовательности функций|**SQLAllocHandle**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011|Невозможно задать атрибут сейчас|**SQLBulkOperations**<br /><br /> **SQLParamData**<br /><br /> **QLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY012|Недопустимый код операции транзакции|**SQLEndTran**|  
|HY013|Ошибка управления памятью|Все функции ODBC, за исключением:<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY014|Достигнут предел количества дескрипторов|**SQLAllocHandle**|  
|HY015|Имена курсоров недоступны|**SQLGetCursorName**|  
|HY016|Не удается изменить дескриптор строки реализации|**SQLCopyDesc**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|Недопустимое использование автоматически выделенного дескриптора|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018|Сервер отклонил запрос отмены|**SQLCancel**|  
|HY019|Несимвольные и недвоичные данные отправлены по частям.|**SQLPutData**|  
|HY020|Попытка присоединить пустое значение|**SQLPutData**|  
|HY021|Неправильные сведения о дескрипторе|**SQLBindParameter**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|Недопустимое значение атрибута|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090|Недопустимая длина строки или буфера|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091|Недопустимый идентификатор поля дескриптора|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092|Недопустимый атрибут идентификатор или параметра|**SQLAllocHandle**<br /><br /> **QLBulkOperations**<br /><br /> **SQLCopyDesc**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetEnvAttr**<br /><br /> **QLParamData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY095|Тип функции за пределами допустимого диапазона|**SQLGetFunctions**|  
|HY096|Недопустимый тип|**SQLGetInfo**|  
|HY097|Тип столбца за пределами допустимого диапазона|**SQLSpecialColumns**|  
|HY098|Тип области вне допустимого диапазона|**SQLSpecialColumns**|  
|HY099|Тип Nullable за пределами диапазона|**SQLSpecialColumns**|  
|HY100|Тип параметра Uniqueness за пределами допустимого диапазона|**SQLStatistics**|  
|HY101|Тип параметра accuracy за пределами допустимого диапазона|**SQLStatistics**|  
|HY103|Недопустимое получение кода|**SQLDataSources**<br /><br /> **SQLDrivers**|  
|HY104|Недопустимое значение точности или масштаба|**SQLBindParameter**|  
|HY105|Недопустимый тип параметра|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|Тип выборки за пределами допустимого диапазона|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HY107|Значение строки за пределами диапазона|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLSetPos**|  
|HY109|Недопустимое положение курсора|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY110|Недопустимое завершение драйвера|**SQLDriverConnect**|  
|HY111|Недопустимый закладок|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HYC00|Дополнительная возможность не реализована|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT00|Время ожидания истекло|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT01|Время ожидания соединения истекло|Все функции ODBC, за исключением:<br /><br /> **SQLDrivers**<br /><br /> **SQLDataSources**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLSetEnvAttr**|  
|IM001|Драйвер не поддерживает эту функцию|Все функции ODBC, за исключением:<br /><br /> **SQLAllocHandle**<br /><br /> **SQLDataSources**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|Имя источника данных не найден и не указан драйвер по умолчанию|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|Не удалось загрузить указанный драйвер|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|Драйвера **SQLAllocHandle** на SQL_HANDLE_ENV сбой|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|Драйвера **SQLAllocHandle** на SQL_HANDLE_DBC сбой|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|Драйвера **SQLSetConnectAttr** сбой|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|Нет источника данных или драйвера задан; Открытие диалогового окна невозможно|**SQLDriverConnect**|  
|IM008|Сбой диалогового окна|**SQLDriverConnect**|  
|IM009|Не удается загрузить трансляции (DLL)|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|Слишком длинное имя источника данных|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|Слишком длинное имя драйвера|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|Синтаксическая ошибка ДРАЙВЕРА ключевое слово|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|Ошибка файла трассировки|Все функции ODBC.|  
|IM014|Недопустимое имя файла источника данных|**SQLDriverConnect**|  
|IM015|Поврежден файл источника данных|**SQLDriverConnect**|
