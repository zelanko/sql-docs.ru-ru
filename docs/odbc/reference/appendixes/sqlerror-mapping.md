---
title: Сопоставление SQLError | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 452ee7b5e2c9e38aaf0fb81969228f5c5e7b5559
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793072"
---
# <a name="sqlerror-mapping"></a>Сопоставление SQLError
Если приложение вызывает **SQLError** через ODBC *3.x* драйвера, вызов метода  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 сопоставляется с  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 с помощью *HandleType* аргумент в значение SQL_HANDLE_ENV, установленным в значение sql_handle_stmt или значение SQL_HANDLE_STMT, соответствующим образом и *обрабатывать* аргументу присвоено значение в *henv*, *hdbc*, или *hstmt*, соответствующим образом. *RecNumber* аргумент, определяется диспетчером драйверов.
