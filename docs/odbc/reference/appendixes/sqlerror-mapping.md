---
title: "Сопоставление SQLError | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1c6cfbf06a9cbbbe635506bbe1e0191879defa1a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlerror-mapping"></a>Сопоставление SQLError
Если приложение вызывает **SQLError** через ODBC 3*.x* драйвера, вызов  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 сопоставляется  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 с *HandleType* аргумент присвоено значение SQL_HANDLE_ENV, установленным в значение sql_handle_stmt или значение SQL_HANDLE_STMT, соответствующим образом и *обработки* аргументу присвоено значение в *henv*, *hdbc*, или *hstmt*соответствующим образом. *RecNumber* аргумент определяется диспетчером драйверов.
