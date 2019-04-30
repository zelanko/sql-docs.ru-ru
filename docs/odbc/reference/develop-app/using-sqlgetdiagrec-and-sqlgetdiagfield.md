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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1db402e7c015ef50ce47b5137e670d9f1836a326
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208433"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Использование SQLGetDiagRec и SQLGetDiagField
Приложения вызывают **SQLGetDiagRec** или **SQLGetDiagField** получения диагностических сведений. Эти функции принимают дескриптор среды, подключения, инструкции или дескриптора и возвращают диагностики из функции, которая последний раз использовали этот дескриптор. Вход в систему определенного дескриптора диагностики отменяются в том случае, когда новая функция вызывается с помощью данного дескриптора. Если функция возвращает несколько диагностических записей, приложение вызывает эти функции несколько раз. Общее число записей состояния получается путем вызова **SQLGetDiagField** для заголовочной записи (запись 0) с параметром SQL_DIAG_NUMBER.  
  
 Приложения получить отдельные поля диагностики, вызвав **SQLGetDiagField** и указав извлекаемого поля. Некоторые диагностические поля не имеют какого-либо значения для определенных типов маркеров. Список полей диагностики и их значения, см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.  
  
 Приложения, извлекать SQLSTATE, собственное значение кода ошибки и диагностическое сообщение в одном вызове путем вызова **SQLGetDiagRec**; **SQLGetDiagRec** не может использоваться для получения сведений из записи заголовка.  
  
 Например следующий код запрашивает у пользователя инструкции SQL и выполняет его. Если любые диагностические сведения, было возвращено, он вызывает **SQLGetDiagField** получить число записей состояния и **SQLGetDiagRec** для получения SQLSTATE, собственное значение кода ошибки и диагностическое сообщение по сравнению с записи.  
  
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
