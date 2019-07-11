---
title: Сопоставление SQLAllocStmt | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1139d87d9f97a3d63236c03e7cf4ced787ad8e85
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793553"
---
# <a name="sqlallocstmt-mapping"></a>Сопоставление SQLAllocStmt
Если приложение вызывает **SQLAllocStmt** через ODBC *3.x* драйвера, вызов метода:  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 сопоставляется с **SQLAllocHandle** диспетчером драйверов в драйвере следующим образом:  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 с помощью *InputHandle* присвоено *hdbc* и *OutputHandlePtr* присвоено *phstmt*.
