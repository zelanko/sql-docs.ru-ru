---
title: "С помощью SQLGetDiagRec и SQLGetDiagField | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3be99267a7b2b5395a03c6a5a03fd9b6c33742e8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>С помощью SQLGetDiagRec и SQLGetDiagField
Приложения вызывают **SQLGetDiagRec** или **SQLGetDiagField** получения диагностических сведений. Эти функции принимают дескриптор среды, соединения, оператор или дескриптор и возвращают диагностики из функции, которая последний раз этот дескриптор. Диагностики, войти в систему определенного дескриптора удаляются, когда новая функция вызывается с помощью данного дескриптора. Если функция вернула нескольких диагностических записей, приложение вызывает эти функции несколько раз. Общее число записей состояния извлекается путем вызова **SQLGetDiagField** записи в заголовке (запись 0) с параметром SQL_DIAG_NUMBER.  
  
 Приложения получить отдельные поля диагностики, вызвав **SQLGetDiagField** и выбора поля для извлечения. Определенные диагностические поля не имеют какого-либо значения для определенных типов маркеров. Список полей диагностики и их значений см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.  
  
 Приложения получают SQLSTATE, машинный код ошибки и диагностическое сообщение в рамках одного вызова путем вызова **SQLGetDiagRec**; **SQLGetDiagRec** не может использоваться для извлечения сведений из запись заголовка.  
  
 Например следующий код запрашивает пользователя для инструкции SQL и выполняет его. Если возвращена все диагностические сведения, он вызывает **SQLGetDiagField** получить число записей состояния и **SQLGetDiagRec** для получения SQLSTATE, машинный код ошибки и диагностическое сообщение по сравнению с записи.  
  
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
   // Get the status records.  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
