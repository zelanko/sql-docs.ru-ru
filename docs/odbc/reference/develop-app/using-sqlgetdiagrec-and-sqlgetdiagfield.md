---
title: Использование SQLGetDiagRec и SQLGetDiagField | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69a17086253b40469b0ed98cb6f870f319f03f52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306755"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Использование SQLGetDiagRec и SQLGetDiagField
Приложения вызывают **SQLGetDiagRec** или **SQLGetDiagField** для получения диагностических сведений. Эти функции принимают среду, соединение, инструкцию или дескриптор дескриптора и возвращают диагностические данные из функции, которая использовалась в последний раз. Диагностика, зарегистрированная в определенном обработчике, отбрасывается при вызове новой функции с помощью этого маркера. Если функция вернула несколько диагностических записей, приложение вызывает эти функции несколько раз. Общее число записей о состоянии извлекается путем вызова **SQLGetDiagField** для записи заголовка (запись 0) с параметром SQL_DIAG_NUMBER.  
  
 Приложения получают отдельные диагностические поля путем вызова **SQLGetDiagField** и указания поля для извлечения. Некоторые диагностические поля не имеют смысла для определенных типов дескрипторов. Список диагностических полей и их значений см. в описании функции [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .  
  
 Приложения извлекают значение SQLSTATE, собственный код ошибки и диагностическое сообщение в одном вызове путем вызова **SQLGetDiagRec**; **SQLGetDiagRec** нельзя использовать для получения сведений из записи заголовка.  
  
 Например, следующий код запрашивает у пользователя инструкцию SQL и выполняет ее. При возвращении любой диагностической информации она вызывает **SQLGetDiagField** для получения количества записей о состоянии и **SQLGetDiagRec** для получения значения SQLSTATE, машинного кода ошибки и диагностического сообщения из этих записей.  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
