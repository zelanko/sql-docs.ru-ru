---
title: Используя СЗЛГетДиагРес и СЗЛГетДиагФилд (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306755"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Использование SQLGetDiagRec и SQLGetDiagField
Приложения, которые вызываются в **s'LGetDiagRec** или **S'LGetDiagField,** чтобы получить диагностическую информацию. Эти функции принимают среду, соединение, оператора или дескрипторную ручку и возвращают диагностику из функции, которая в последний раз использовалась этой ручкой. Диагностика, зарегистрированная на определенной ручке, отбрасывается, когда новая функция называется с помощью этой ручки. Если функция вернула несколько диагностических записей, приложение вызывает эти функции несколько раз; общее количество записей о состоянии извлекается, вызывая **s'LGetDiagField** для записи заголовка (запись 0) с SQL_DIAG_NUMBER опцией.  
  
 Приложения получают отдельные диагностические поля, позвонив по **телефону S'LGetDiagField** и указав поле для извлечения. Некоторые диагностические поля не имеют никакого значения для определенных типов ручек. Список диагностических полей и их значений можно ознакомьтесь с описанием функции [S'LGetDiagField.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
 Приложения получают s'LSTATE, родной код ошибки и диагностическое сообщение в одном вызове, позвонив по **телефону S'LGetDiagRec;** Для получения информации из записи заголовка не может использоваться система **S'LGetDiagRec.**  
  
 Например, следующий код подсказывает пользователю заявление s'L и выполняет ее. Если какая-либо диагностическая информация была возвращена, она вызывает **S'LGetDiagField,** чтобы получить номер записей о состоянии и **S'LGetDiagRec,** чтобы получить из этих записей код ошибки, родной код ошибки и диагностическое сообщение.  
  
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
