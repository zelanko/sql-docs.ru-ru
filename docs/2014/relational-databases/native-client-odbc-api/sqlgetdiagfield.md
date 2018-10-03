---
title: SQLGetDiagField | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDiagField function
ms.assetid: 395245ba-0372-43ec-b9a4-a29410d85a6d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20b84484500e338136ff0ab99af7890d06a466e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109524"
---
# <a name="sqlgetdiagfield"></a>SQLGetDiagField
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента заданы следующие дополнительные поля для `SQLGetDiagField`. Эти поля поддерживают множество отчетов об ошибках для приложений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и доступны во всех диагностических записях, созданных дескрипторами соединения ODBC и дескрипторами инструкций ODBC. Эти поля определены в файле sqlncli.h.  
  
|Поля диагностических записей|Описание|  
|------------------------------|-----------------|  
|SQL_DIAG_SS_LINE|Сообщает номер строки хранимой процедуры, на которой произошла ошибка. Значение SQL_DIAG_SS_LINE значимо, только если SQL_DIAG_SS_PROCNAME возвращает значение. Значение возвращается как 16-разрядное целое число без знака.|  
|SQL_DIAG_SS_MSGSTATE|Состояние сообщения об ошибке. Сведения о состоянии сообщения об ошибке, см. в разделе [RAISERROR](/sql/t-sql/language-elements/raiserror-transact-sql). Значение возвращается как 32-разрядное целое число со знаком.|  
|SQL_DIAG_SS_PROCNAME|Имя хранимой процедуры, в которой возникла ошибка, если это имеет смысл. Значение возвращается как символьная строка. Максимальная длина строки (в символах) зависит от версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ее можно определить путем вызова [SQLGetInfo](sqlgetinfo.md) запрашивая значение sql_max_procedure_name_len.|  
|SQL_DIAG_SS_SEVERITY|Степень серьезности связанного сообщения об ошибке. Значение возвращается как 32-разрядное целое число со знаком.|  
|SQL_DIAG_SS_SRVNAME|Имя сервера, на котором произошла ошибка. Значение возвращается как символьная строка. Длина строки (в символах) задается макросом SQL_MAX_SQLSERVERNAME в файле sqlncli.h.|  
  
 Специальные диагностические поля [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], содержащие символьные данные, SQL_DIAG_SS_PROCNAME и SQL_DIAG_SS_SRVNAME, возвращают эти данные клиенту как строки в ANSI, строки в Юникоде или строки, оканчивающиеся нулевым байтом. Если необходимо, счетчик символов должен быть изменен с учетом ширины символа. Также можно использовать переносимый тип данных C, такой как TCHAR или SQLTCHAR, чтобы удостовериться, что программная переменная имеет правильную длину.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает следующие дополнительные коды динамических функций, содержащие последнюю попытку выполнения инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Код динамической функции возвращается в заголовке (запись 0) диагностического набора записей и доступен при каждом выполнении (успешном или нет).  
  
|Код динамической функции|Source|  
|---------------------------|------------|  
|SQL_DIAG_DFC_SS_ALTER_DATABASE|ALTER DATABASE, инструкция|  
|SQL_DIAG_DFC_SS_CHECKPOINT|CHECKPOINT, инструкция|  
|SQL_DIAG_DFC_SS_CONDITION|Ошибка происходит в предложениях WHERE или HAVING инструкции.|  
|SQL_DIAG_DFC_SS_CREATE_DATABASE|Инструкция CREATE DATABASE|  
|SQL_DIAG_DFC_SS_CREATE_DEFAULT|Инструкция CREATE DEFAULT|  
|SQL_DIAG_DFC_SS_CREATE_PROCEDURE|CREATE PROCEDURE, инструкция|  
|SQL_DIAG_DFC_SS_CREATE_RULE|CREATE RULE, инструкция|  
|SQL_DIAG_DFC_SS_CREATE_TRIGGER|CREATE TRIGGER, инструкция|  
|SQL_DIAG_DFC_SS_CURSOR_DECLARE|DECLARE CURSOR, инструкция|  
|SQL_DIAG_DFC_SS_CURSOR_OPEN|OPEN, инструкция|  
|SQL_DIAG_DFC_SS_CURSOR_FETCH|FETCH, инструкция|  
|SQL_DIAG_DFC_SS_CURSOR_CLOSE|Инструкция CLOSE|  
|SQL_DIAG_DFC_SS_DEALLOCATE_CURSOR|DEALLOCATE, инструкция|  
|SQL_DIAG_DFC_SS_DBCC|Инструкция DBCC|  
|SQL_DIAG_DFC_SS_DENY|DENY, инструкция|  
|SQL_DIAG_DFC_SS_DROP_DATABASE|DROP DATABASE, инструкция|  
|SQL_DIAG_DFC_SS_DROP_DEFAULT|DROP DEFAULT, инструкция|  
|SQL_DIAG_DFC_SS_DROP_PROCEDURE|Инструкция DROP PROCEDURE|  
|SQL_DIAG_DFC_SS_DROP_RULE|DROP RULE, инструкция|  
|SQL_DIAG_DFC_SS_DROP_TRIGGER|Инструкция DROP TRIGGER|  
|SQL_DIAG_DFC_SS_DUMP_DATABASE|Инструкция BACKUP или DUMP DATABASE|  
|SQL_DIAG_DFC_SS_DUMP_TABLE|Инструкция DUMP TABLE|  
|SQL_DIAG_DFC_SS_DUMP_TRANSACTION|Инструкция BACKUP или DUMP TRANSACTION. Также возвращается для инструкции CHECKPOINT, если **trunc. log на контрольной точке.** базы данных включен.|  
|SQL_DIAG_DFC_SS_GOTO|Инструкция управления потоком GOTO|  
|SQL_DIAG_DFC_SS_INSERT_BULK|Инструкция INSERT BULK|  
|SQL_DIAG_DFC_SS_KILL|Инструкция KILL|  
|SQL_DIAG_DFC_SS_LOAD_DATABASE|Инструкция LOAD или RESTORE DATABASE|  
|SQL_DIAG_DFC_SS_LOAD_HEADERONLY|Инструкция LOAD или RESTORE HEADERONLY|  
|SQL_DIAG_DFC_SS_LOAD_TABLE|Инструкция LOAD TABLE|  
|SQL_DIAG_DFC_SS_LOAD_TRANSACTION|Инструкция LOAD или RESTORE TRANSACTION|  
|SQL_DIAG_DFC_SS_PRINT|PRINT, инструкция|  
|SQL_DIAG_DFC_SS_RAISERROR|RAISERROR, инструкция|  
|SQL_DIAG_DFC_SS_READTEXT|READTEXT, инструкция|  
|SQL_DIAG_DFC_SS_RECONFIGURE|RECONFIGURE, инструкция|  
|SQL_DIAG_DFC_SS_RETURN|Инструкция управления потоком RETURN|  
|SQL_DIAG_DFC_SS_SELECT_INTO|SELECT INTO, инструкция|  
|SQL_DIAG_DFC_SS_SET|Инструкция SET (общая, все параметры)|  
|SQL_DIAG_DFC_SS_SET_IDENTITY_INSERT|SET IDENTITY_INSERT, инструкция|  
|SQL_DIAG_DFC_SS_SET_ROW_COUNT|SET ROWCOUNT, инструкция|  
|SQL_DIAG_DFC_SS_SET_STATISTICS|Инструкция SET STATISTICS IO или SET STATISTICS TIME|  
|SQL_DIAG_DFC_SS_SET_TEXTSIZE|SET TEXTSIZE, инструкция|  
|SQL_DIAG_DFC_SS_SETUSER|SETUSER, инструкция|  
|SQL_DIAG_DFC_SS_SET_XCTLVL|SET TRANSACTION ISOLATION LEVEL, инструкция|  
|SQL_DIAG_DFC_SS_SHUTDOWN|SHUTDOWN, инструкция|  
|SQL_DIAG_DFC_SS_TRANS_BEGIN|Инструкция BEGIN TRAN|  
|SQL_DIAG_DFC_SS_TRANS_COMMIT|Инструкция COMMIT TRAN|  
|SQL_DIAG_DFC_SS_TRANS_PREPARE|Подготовка к фиксации распределенной транзакции|  
|SQL_DIAG_DFC_SS_TRANS_ROLLBACK|Инструкция ROLLBACK TRAN|  
|SQL_DIAG_DFC_SS_TRANS_SAVE|Инструкция SAVE TRAN|  
|SQL_DIAG_DFC_SS_TRUNCATE_TABLE|TRUNCATE TABLE, инструкция|  
|SQL_DIAG_DFC_SS_UPDATE_STATISTICS|инструкция UPDATE STATISTICS|  
|SQL_DIAG_DFC_SS_UPDATETEXT|UPDATETEXT, инструкция|  
|SQL_DIAG_DFC_SS_USE|USE, инструкция|  
|SQL_DIAG_DFC_SS_WAITFOR|Инструкция управления потоком WAITFOR|  
|SQL_DIAG_DFC_SS_WRITETEXT|WRITETEXT, инструкция|  
  
## <a name="sqlgetdiagfield-and-table-valued-parameters"></a>Функция SQLGetDiagField и возвращающие табличное значение параметры  
 SQLGetDiagField может использоваться для получения двух диагностических полей: SQL_DIAG_SS_TABLE_COLUMN_NUMBER и SQL_DIAG_SS_TABLE_ROW_NUMBER. Эти поля помогают определить, какое значение вызвало ошибку или предупреждение, связанные с диагностической записью.  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLGetDiagField](http://go.microsoft.com/fwlink/?LinkId=59352)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
