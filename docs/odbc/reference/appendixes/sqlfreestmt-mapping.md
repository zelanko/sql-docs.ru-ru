---
title: "Сопоставление SQLFreeStmt | Документы Microsoft"
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
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c4764fbae07fe1e41c576b14a444dc8b28cf730e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlfreestmt-mapping"></a>Сопоставление SQLFreeStmt
Если приложение вызывает **SQLFreeStmt** с *параметр* аргумент SQL_DROP через ODBC 3*.x* драйвера, вызов  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 сопоставляется  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 с *обработки* аргументу присвоено значение в *hstmt*.
