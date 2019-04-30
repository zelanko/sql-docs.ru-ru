---
title: Инструкции SQL, введенный пользователем | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 28256433802d686f4362b2b733fc2d2b13e65302
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149137"
---
# <a name="sql-statements-entered-by-the-user"></a>Инструкции SQL, введенные пользователем
Приложения, которые обычно выполняют специализированный анализ позволяют пользователю вводить инструкции SQL непосредственно. Пример:  
  
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
  
 Такой подход упрощает кодирования приложения; приложение полагается на пользователей для создания инструкции SQL и в источнике данных, чтобы проверить допустимость инструкции. Так как это сложно написать графический пользовательский интерфейс, который адекватно предоставляет особенностей SQL, просто спросив пользователю ввести текст инструкции SQL может быть более предпочтительным по сравнению. Тем не менее для этого пользователю знать не только SQL, но схема запрашиваемым источником данных. Некоторые приложения предоставляют графический пользовательский интерфейс, по которому пользователь может выполнять основные инструкция SQL create и также предоставляют интерфейс текста, с помощью которого пользователь может изменить его.
