---
description: Приложение А. Коды ошибок ODBC
title: Приложение а. коды ошибок ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error codes [ODBC]
- SQLSTATE [ODBC]
- error codes [ODBC], SQLSTATE
ms.assetid: c06902e4-721d-42e2-b818-05f0e18e4ce0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a587578ba74cd2ed36a919953000190a6274b62d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411554"
---
# <a name="appendix-a-odbc-error-codes"></a>Приложение А. Коды ошибок ODBC
В этом разделе обсуждаются значения SQLSTATE для ODBC 3. *x*. Дополнительные сведения об ODBC 3. значения *x* SQLSTATE см. в разделе [сопоставления SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md).  
  
 **SQLGetDiagRec** или **SQLGETDIAGFIELD** возвращает значения SQLSTATE в соответствии с определением Open Group *Управление данными: язык SQL (SQL), версия 2* (март 1995). Значения SQLSTATE — это строки, содержащие пять символов. В следующей таблице перечислены значения SQLSTATE, которые драйвер может вернуть для **SQLGetDiagRec**.  
  
 Символьная строка, возвращаемая для SQLSTATE, состоит из значения класса из двух символов, за которым следует значение подкласса из трех символов. Значение класса "01" указывает на предупреждение и сопровождается кодом возврата SQL_SUCCESS_WITH_INFO. Значения класса, отличные от "01", за исключением класса "IM", указывают на ошибку и могут сопровождаться возвращаемым значением SQL_ERROR. Класс IM характерен для предупреждений и ошибок, производных от реализации самого ODBC. Значение подкласса "000" в любом классе указывает на отсутствие подкласса для этого SQLSTATE. Назначение значений класса и подкласса определяется SQL-92.  
  
> [!NOTE]  
>  Хотя успешное выполнение функции обычно обозначается возвращаемым значением SQL_SUCCESS, 00000 SQLSTATE также указывает на успех.  
  
|SQLSTATE|Ошибка|Можно вернуть из|  
|--------------|-----------|--------------------------|  
|01000|Общее предупреждение|Все функции ODBC, кроме:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|01001|Конфликт операций с курсором|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|01002|Ошибка отключения|**SQLDisconnect**|  
|01003|Значение NULL исключено в функции Set|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|Строковые данные, усеченные справа|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **склнативе**<br /><br /> **Метод SQLParamData SQL**<br /><br /> **SQLPutData**<br /><br /> **SQLSetCursorName**|  
|01006|Привилегия не отменена|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|Привилегия не предоставлена|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|Недопустимый атрибут строки подключения|**SQLBrowseConnect**<br /><br /> **склдриверконнек**|  
|01S01|Ошибка в строке|**SQLBulkOperations**<br /><br /> **SQLExtendedFetch**<br /><br /> **функция SQLSetPos;**|  
|01S02|Значение параметра изменено|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01S06|Попытка выборки до того, как результирующий набор вернул первый набор строк|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|01S07|Усечение дробной части|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|01S08|Ошибка при сохранении файлового DSN|**SQLDriverConnect**|  
|01S09|Недопустимое ключевое слово|**SQLDriverConnect**|  
|07001|Неправильное число параметров|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|Неверное поле количества|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|Подготовленная инструкция не является *спецификацией курсора*|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|Нарушение атрибута ограниченного типа данных|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|07009|Недопустимый индекс дескриптора|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **склсетдескрексклсетпос**|  
|07S01|Недопустимое использование параметра по умолчанию|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|Клиенту не удалось установить подключение|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|Имя подключения используется|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|Соединение не открыто|**Функцию SQLAllocHandle**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|Сервер отклонил подключение|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|Сбой подключения во время транзакции|**SQLEndTran**|  
|08S01|Сбой канала связи|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **склкопидеск**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21S01|Список вставляемых значений не соответствует списку столбцов|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21S02|Степень производной таблицы не соответствует списку столбцов|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **функция SQLSetPos;**|  
|22001|Строковые данные, усеченные справа|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **функция SQLSetPos;**|  
|22002|Требуемая, но не определенная переменная индикатора|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|Числовое значение вне допустимого диапазона|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22007|Недопустимый формат даты и времени|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22008|Переполнение поля даты и времени|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **клпарамдата**<br /><br /> **SQLPutData**|  
|22012|Деление на ноль|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|Переполнение поля интервала|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22018|Недопустимое символьное значение для спецификации приведения|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22019|Недопустимый escape-символ|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|Недопустимая escape-последовательность|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|Строковые данные, несовпадение длины|**SQLParamData**|  
|23000|Нарушение ограничения целостности|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|24 000|Недопустимое состояние курсора|**SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|Недопустимое состояние транзакции|**SQLDisconnect**|  
|25S01|Состояние транзакции|**SQLEndTran**|  
|25S02|Транзакция все еще активна|**SQLEndTran**|  
|25S03|Выполняется откат транзакции|**SQLEndTran**|  
|28000|Недопустимая спецификация авторизации|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|Недопустимое имя курсора|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetCursorName**|  
|3C000|Повторяющееся имя курсора|**SQLSetCursorName**|  
|3D000|Недопустимое имя каталога|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F000|Недопустимое имя схемы|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|Сбой сериализации|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|Нарушение ограничения целостности|**SQLEndTran**|  
|40003|Неизвестное завершение инструкции|**SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|Синтаксическая ошибка или нарушение прав доступа|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **функция SQLSetPos;**|  
|42S01|Базовая таблица или представление уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S02|Базовая таблица или представление не найдены|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S11|Индекс уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S12|Индекс не найден|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S21|Столбец уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S22|Столбец не найден|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|Нарушение параметра WITH CHECK OPTION|**SQLBulkOperations**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|HY000|Общая ошибка|Все функции ODBC, кроме:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|HY001|Ошибка выделения памяти|Все функции ODBC, кроме:<br /><br /> **SQLError**<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|HY003|Недопустимый тип буфера приложения|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|Недопустимый тип данных SQL|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|Связанная инструкция не подготовлена|**склкопидеск**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008|Operation canceled|Все функции ODBC, которые могут обрабатываться асинхронно:<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|Недопустимое использование пустого указателя|**Функцию SQLAllocHandle**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|Ошибка последовательности функций|**Функцию SQLAllocHandle**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **склкопидеск**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **Функция SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011|Задать атрибут сейчас невозможно|**SQLBulkOperations**<br /><br /> **SQLParamData**<br /><br /> **клсетпос**<br /><br /> **SQLSetStmtAttr**|  
|HY012|Недопустимый код операции транзакции|**SQLEndTran**|  
|HY013|Ошибка управления памятью|Все функции ODBC, кроме:<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|HY014|Превышено ограничение на количество дескрипторов|**Функцию SQLAllocHandle**|  
|HY015|Нет доступных имен курсоров|**SQLGetCursorName**|  
|HY016|Невозможно изменить дескриптор строки реализации|**склкопидеск**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|Недопустимое использование автоматически выделенного дескриптора дескриптора|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018|Сервер отклонил запрос на отмену|**SQLCancel**|  
|HY019|Несимвольные и недвоичные данные, отправляемые частями|**SQLPutData**|  
|HY020|Попытка сцепления значения NULL|**SQLPutData**|  
|HY021|Непоследовательные сведения о дескрипторе|**SQLBindParameter**<br /><br /> **склкопидеск**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|Недопустимое значение атрибута|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090|Недопустимая длина строки или буфера|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091|Недопустимый идентификатор поля дескриптора|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092|Недопустимый идентификатор атрибута или параметра|**Функцию SQLAllocHandle**<br /><br /> **клбулкоператионс**<br /><br /> **склкопидеск**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **Функция SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetEnvAttr**<br /><br /> **клпарамдата**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**|  
|HY095|Тип функции вне допустимого диапазона|**SQLGetFunctions**|  
|HY096|Недопустимый тип данных|**SQLGetInfo**|  
|HY097|Тип столбца вне допустимого диапазона|**SQLSpecialColumns**|  
|HY098|Тип области вне допустимого диапазона|**SQLSpecialColumns**|  
|HY099|Тип Nullable вне допустимого диапазона|**SQLSpecialColumns**|  
|HY100|Тип параметра уникальности выходит за пределы допустимого диапазона|**SQLStatistics**|  
|HY101|Тип параметра точности вне допустимого диапазона|**SQLStatistics**|  
|HY103|Недопустимый код получения|**SQLDataSources**<br /><br /> **SQLDrivers**|  
|HY104|Недопустимое значение точности или масштаба|**SQLBindParameter**|  
|HY105|Недопустимый тип параметра|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|Тип выборки вне допустимого диапазона|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HY107|Значение строки вне допустимого диапазона|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **функция SQLSetPos;**|  
|HY109|Недопустимое расположение курсора|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|HY110|Недопустимое завершение драйвера|**SQLDriverConnect**|  
|HY111|Недопустимое значение закладки|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HYC00|Необязательная функция не реализована|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT00|Время ожидания истекло|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT01|Время ожидания подключения истекло|Все функции ODBC, кроме:<br /><br /> **SQLDrivers**<br /><br /> **SQLDataSources**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLSetEnvAttr**|  
|IM001|Драйвер не поддерживает эту функцию|Все функции ODBC, кроме:<br /><br /> **Функцию SQLAllocHandle**<br /><br /> **SQLDataSources**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|Имя источника данных не найдено, драйвер по умолчанию не указан|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|Не удалось загрузить указанный драйвер|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|Сбой **функцию SQLAllocHandle** драйвера на SQL_HANDLE_ENV|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|Сбой **функцию SQLAllocHandle** драйвера на SQL_HANDLE_DBC|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|Сбой **SQLSetConnectAttr** драйвера|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|Не указан источник данных или драйвер. диалоговое окно запрещено|**SQLDriverConnect**|  
|IM008|Сбой диалогового окна|**SQLDriverConnect**|  
|IM009|Не удалось загрузить библиотеку DLL для перевода|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|Слишком длинное имя источника данных|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|Слишком длинное имя драйвера|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|Ошибка синтаксиса ключевого слова DRIVER|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|Ошибка файла трассировки|Все функции ODBC.|  
|IM014|Недопустимое имя файлового DSN|**SQLDriverConnect**|  
|IM015|Поврежденный файловый источник данных|**SQLDriverConnect**|
