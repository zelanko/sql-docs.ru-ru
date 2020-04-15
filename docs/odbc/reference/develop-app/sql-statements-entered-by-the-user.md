---
title: Заявления, внесенные пользователем( Документы Майкрософт
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
ms.openlocfilehash: bf2f8cf36be392cb42a970fa2fb0b19c35daeb39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301965"
---
# <a name="sql-statements-entered-by-the-user"></a>Инструкции SQL, введенные пользователем
Приложения, выполняющие специальный анализ, также обычно позволяют пользователю вводить операторы S'L напрямую. Пример:  
  
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
  
 Такой подход упрощает кодирование приложений; приложение полагается на пользователя для создания оператора S'L и на источник данных для проверки достоверности оператора. Поскольку трудно написать графический пользовательский интерфейс, который адекватно разоблачает тонкости S'L, просто просить пользователя ввести текст заявления S'L может быть предпочтительной альтернативой. Однако это требует, чтобы пользователь знал не только S'L, но и схему запрашиваемого источника данных. Некоторые приложения предоставляют графический пользовательский интерфейс, с помощью которого пользователь может создать базовое заявление s'L, а также предоставить текстовый интерфейс, с помощью которого пользователь может изменить его.
