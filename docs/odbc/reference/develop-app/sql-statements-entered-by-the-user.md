---
title: Инструкции SQL, вводимых пользователем | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 78a1653df60b21cde772cbe32a688b3fdef80a42
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086075"
---
# <a name="sql-statements-entered-by-the-user"></a>Инструкции SQL, введенные пользователем
Приложения, выполняющие автоматизированный анализ, обычно позволяют пользователю непосредственно вводить инструкции SQL. Пример:  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 Такой подход упрощает написание кода приложения. приложение полагается на пользователя, чтобы создать инструкцию SQL и источник данных для проверки действительности инструкции. Поскольку трудно написать графический пользовательский интерфейс, который адекватно предоставляет сложные структуры SQL, просто запросив пользователя ввести текст инструкции SQL может быть предпочтительным вариантом. Однако это требует, чтобы пользователь знал не только SQL, но также схему запрашиваемого источника данных. Некоторые приложения предоставляют графический пользовательский интерфейс, с помощью которого пользователь может создать базовую инструкцию SQL, а также предоставляет текстовый интерфейс, с помощью которого пользователь может изменить его.
