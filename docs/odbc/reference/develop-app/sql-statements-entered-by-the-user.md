---
description: Инструкции SQL, введенные пользователем
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d7d7ee7ffc2a4c949173c3eee888e4c41b9e741
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424546"
---
# <a name="sql-statements-entered-by-the-user"></a>Инструкции SQL, введенные пользователем
Приложения, выполняющие автоматизированный анализ, обычно позволяют пользователю непосредственно вводить инструкции SQL. Например:  
  
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
