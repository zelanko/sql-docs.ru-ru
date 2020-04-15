---
title: 'Приложение A: Коды ошибки ODBC Документы Майкрософт'
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
ms.openlocfilehash: af288cf9f0564f6fe0dbef14f66143667120c656
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307525"
---
# <a name="appendix-a-odbc-error-codes"></a>Приложение А. Коды ошибок ODBC
В этой теме обсуждаются значения S'LSTATE для ODBC 3. *x*. Для получения дополнительной информации о ODBC 3. *х* значения S'LSTATE, [см.](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
 **СЗЛГетДиагРе** или **СЗЛГетДиагФилд** возвращает значения S'Lstate, как это определено в Open Group *Data Management: Структурированный язык запросов (S'L), версия 2* (март 1995 года). Значения S'LSTATE являются строками, которые содержат пять символов. В следующей таблице перечислены значения, которые водитель может вернуть на **s'LGetDiagRec.**  
  
 Значение строки символов, возвращенное для S'LSTATE, состоит из значения класса два символа, за которым следует значение подкласса из трех символов. Значение класса "01" указывает на предупреждение и сопровождается обратным кодом SQL_SUCCESS_WITH_INFO. Значения класса, кроме "01", за исключением класса "IM", указывают на ошибку и сопровождаются значением возврата SQL_ERROR. Класс "IM" специфичен для предупреждений и ошибок, которые вытекают из реализации самого ODBC. Значение подкласса "000" в любом классе указывает на отсутствие подкласса для этого S'LSTATE. Назначение значений класса и подкласса определяется СЗЛ-92.  
  
> [!NOTE]  
>  Несмотря на то, что успешное выполнение функции обычно указывается на возвратное значение SQL_SUCCESS, S'LSTATE 00000 также указывает на успех.  
  
|SQLSTATE|Error|Может быть возвращен из|  
|--------------|-----------|--------------------------|  
|01000|Общее предупреждение|Все функции ODBC, за исключением:<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|01001|Конфликт операции Cursor|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|01002|Ошибка отключения|**СЗЛДИСКоннект**|  
|01003|Null значение устранено в наборе функции|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|Строковые данные, право-усеченные|**SQLBrowseConnect**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColAttribute**<br /><br /> **Источники данных S'LData**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **СЗЛГетЕнвТтр**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **СЗЛНатив**<br /><br /> **СЗЛПарамДата**<br /><br /> **SQLPutData**<br /><br /> **СЗЛСетКурсОрНамейм**|  
|01006|Привилегия не отменена|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|Привилегия не предоставляется|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|Недействительный атрибут строки соединения|**SQLBrowseConnect**<br /><br /> **СЗЛДрайверКоннек**|  
|01S01|Ошибка в строке|**СЗЛБалКОперации**<br /><br /> **Sqlextendedfetch**<br /><br /> **функция SQLSetPos;**|  
|01S02|Изменение значения опциона|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01S06|Попытка получить до того, как набор результатов вернет первый ряд|**Sqlextendedfetch**<br /><br /> **SQLFetchScroll**|  
|01S07|Фракционная усечение|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|01S08|Сохранение ошибки файла DSN|**SQLDriverConnect**|  
|01S09|Недействительные ключевые слова|**SQLDriverConnect**|  
|07001|Неправильное количество параметров|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|Поле COUNT неправильное|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|Подготовленное заявление не является *спецификацией курсора*|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|Нарушение атрибута типа ограниченного доступа|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|07009|Недействительный индекс дескриптора|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **СЗЛСетДескССС-СКВЕТПоС**|  
|07S01|Недействительное использование параметра по умолчанию|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|Клиент не может установить соединение|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|Имя соединения в использовании|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|Подключение не открыто|**СЗЛАллокХэндл**<br /><br /> **СЗЛДИСКоннект**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|Сервер отклонил соединение|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|Сбой подключения во время транзакции|**SQLEndTran**|  
|08S01|Сбой связи|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **СЗЛКопиДеск**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21S01|Список значений вставки не соответствует списку столбцов|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21S02|Степень производной таблицы не соответствует списку столбцов|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **функция SQLSetPos;**|  
|22001|Строковые данные, право-усеченные|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **функция SQLSetPos;**|  
|22002|Переменная переменная индикатора требуется, но не поставляется|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|Числовое значение вне диапазона|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22007|Недействительный формат дата-времени|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22008|Переполниние полей datetime|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **LParamData**<br /><br /> **SQLPutData**|  
|22012|Разделение на ноль|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|Переполниние поля интервала|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22018|Недействительное значение символов для спецификации литья|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **функция SQLSetPos;**|  
|22019|Недействительный персонаж побега|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|Недействительная последовательность побега|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|Строковые данные, несовпадение длины|**SQLParamData**|  
|23000|Нарушение ограничения целостности|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|24 000|Недопустимое состояние курсора|**СЗЛБалКОперации**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **СЗЛСетКурсОрНамейм**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|Недопустимое состояние транзакции|**СЗЛДИСКоннект**|  
|25S01|Состояние транзакции|**SQLEndTran**|  
|25S02|Транзакция по-прежнему активна|**SQLEndTran**|  
|25S03|Транзакция откатывается назад|**SQLEndTran**|  
|28000|Недействительная спецификация авторизации|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|Недопустимое имя курсора|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **СЗЛСетКурсОрНамейм**|  
|3C000|Двойное имя курсора|**СЗЛСетКурсОрНамейм**|  
|3D000|Недействительное название каталога|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F000|Имя недействительной схемы|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|Сбой сериализации|**СЗЛБалКОперации**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|Нарушение ограничения целостности|**SQLEndTran**|  
|40003|Завершение заявления неизвестно|**СЗЛБалКОперации**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|Ошибка синтаксиса или нарушение доступа|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **функция SQLSetPos;**|  
|42S01|Базовая таблица или представление уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S02|Базовая таблица или представление не найдено|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S11|Индекс уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S12|Индекс не найден|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S21|Колонка уже существует|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S22|Колонка не найдена|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|Нарушение параметра WITH CHECK OPTION|**СЗЛБалКОперации**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|HY000|Общая ошибка|Все функции ODBC, за исключением:<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|HY001|Ошибка распределения памяти|Все функции ODBC, за исключением:<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|HY003|Недействительный тип буфера приложения|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|Недействительный тип данных S'L|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|Связанное заявление не подготовлено|**СЗЛКопиДеск**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008|Operation canceled|Все функции ODBC, которые могут быть обработаны асинхронно:<br /><br /> **SQLBrowseConnect**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **СЗЛДИСКоннект**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|Недействительное использование нулевой указатель|**СЗЛАллокХэндл**<br /><br /> **SQLBindParameter**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **СЗЛСетКурсОрНамейм**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|Ошибка последовательности функций|**СЗЛАллокХэндл**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **СЗЛКопиДеск**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **СЗЛДИСКоннект**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **Функция SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **СЗЛСетКурсОрНамейм**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011|Атрибут не может быть установлен сейчас|**СЗЛБалКОперации**<br /><br /> **SQLParamData**<br /><br /> **ЗЛСетПоС**<br /><br /> **SQLSetStmtAttr**|  
|HY012|Недействительный код операции транзакции|**SQLEndTran**|  
|HY013|Ошибка управления памятью|Все функции ODBC, за исключением:<br /><br /> **SQLGetDiagField**<br /><br /> **Функции SQLGetDiagRec**|  
|HY014|Превышение лимита на количество ручек|**СЗЛАллокХэндл**|  
|HY015|Имя курсора недоступно|**SQLGetCursorName**|  
|HY016|Не удается изменить дескриптор строки реализации|**СЗЛКопиДеск**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|Недействительное использование автоматической дескрипторной ручки|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018|Сервер отклонил запрос на отмену|**SQLCancel**|  
|HY019|Нехарактерные и небинарные данные, отправленные по частям|**SQLPutData**|  
|HY020|Попытка совмещеть нулевую стоимость|**SQLPutData**|  
|HY021|Несогласованная информация о дескрипторе|**SQLBindParameter**<br /><br /> **СЗЛКопиДеск**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|Значение недействительных атрибутов|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090|Недействительная длина строки или буфера|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **Источники данных S'LData**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **СЗЛСетКурсОрНамейм**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091|Идентификатор полей недействительных дескрипторов|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092|Недействительный идентификатор атрибута/опциона|**СЗЛАллокХэндл**<br /><br /> **ЗлБалкОперации**<br /><br /> **СЗЛКопиДеск**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **Функция SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **СЗЛГетЕнвТтр**<br /><br /> **LParamData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**|  
|HY095|Тип функции вне диапазона|**SQLGetFunctions**|  
|HY096|Недействительный тип информации|**SQLGetInfo**|  
|HY097|Тип столбца вне диапазона|**SQLSpecialColumns**|  
|HY098|Тип области вне диапазона|**SQLSpecialColumns**|  
|HY099|Nullable тип вне диапазона|**SQLSpecialColumns**|  
|HY100|Тип опции уникальности вне диапазона|**SQLStatistics**|  
|HY101|Тип параметра точности вне диапазона|**SQLStatistics**|  
|HY103|Недействительный код поиска|**Источники данных S'LData**<br /><br /> **SQLDrivers**|  
|HY104|Недействительное значение точности или масштаба|**SQLBindParameter**|  
|HY105|Недействительный тип параметра|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|Тип извне диапазона|**Sqlextendedfetch**<br /><br /> **SQLFetchScroll**|  
|HY107|Значение строки вне диапазона|**Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **функция SQLSetPos;**|  
|HY109|Положение недействительного курсора|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **функция SQLSetPos;**|  
|HY110|Недействительное завершение работы драйвера|**SQLDriverConnect**|  
|HY111|Недействительная стоимость закладки|**Sqlextendedfetch**<br /><br /> **SQLFetchScroll**|  
|HYC00|Дополнительная функция не реализована|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **СЗЛГетЕнвТтр**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT00|Время ожидания истекло|**SQLBrowseConnect**<br /><br /> **СЗЛБалКОперации**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **Sqlextendedfetch**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **функция SQLSetPos;**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT01|Срок истечения времени подключения|Все функции ODBC, за исключением:<br /><br /> **SQLDrivers**<br /><br /> **Источники данных S'LData**<br /><br /> **СЗЛГетЕнвТтр**<br /><br /> **SQLSetEnvAttr**|  
|IM001|Драйвер не поддерживает эту функцию|Все функции ODBC, за исключением:<br /><br /> **СЗЛАллокХэндл**<br /><br /> **Источники данных S'LData**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|Имя источника данных не найдено и не указан драйвер по умолчанию|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|Указанный драйвер не может быть загружен|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|Водитель **S'LAllocHandle** на SQL_HANDLE_ENV не удалось|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|Водитель **S'LAllocHandle** на SQL_HANDLE_DBC не удалось|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|Сбой **драйвера s'LSetConnectAttr**|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|Источник данных или драйвер не указаны; диалог запрещен|**SQLDriverConnect**|  
|IM008|Диалог не удалось|**SQLDriverConnect**|  
|IM009|Невозможно загрузить перевод DLL|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|Имя источника данных слишком длинное|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|Имя водителя слишком длинное|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|Driver ошибка синтаксиса ключевых слов|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|Ошибка файла трассировки|Все функции ODBC.|  
|IM014|Недействительное название файла DSN|**SQLDriverConnect**|  
|IM015|Поврежденный источник данных файлов|**SQLDriverConnect**|
