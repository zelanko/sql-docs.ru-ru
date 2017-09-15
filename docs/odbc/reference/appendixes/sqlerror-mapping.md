---
title: "Сопоставление SQLError | Документы Microsoft"
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
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ebbe17713149276acbe061bfb8ba41503026306
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
