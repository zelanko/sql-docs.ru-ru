---
title: "Инструкции SQL, введенные пользователем | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b234123c01d4bdf4590c000b996a4febe4ad485e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sql-statements-entered-by-the-user"></a>Инструкции SQL, введенный пользователем
Приложения, которые также часто выполнять нерегламентированный анализ разрешить пользователю прямого ввода инструкций SQL. Например:  
  
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
  
 Такой подход также упрощает кодирования приложения; приложение зависит от пользователя для создания инструкции SQL и источника данных, чтобы проверить допустимость инструкции. Поскольку это затрудняет создание графический пользовательский интерфейс, представляющий адекватно особенностей SQL, просто попросить пользователя ввести текст инструкции SQL может быть более предпочтительным вариантом. Однако для этого требуется пользователю возможность узнать, не только SQL, но схема запрашиваемым источником данных. Некоторые приложения предоставляют графический пользовательский интерфейс, с помощью которого пользователь может создать инструкцию SQL и также предоставить интерфейс текста, с помощью которого пользователь может изменить его.
