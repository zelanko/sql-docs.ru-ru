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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 447233a3ba014a5ef92f2f49840ad302f8aeccf0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305487"
---
# <a name="sqlallocstmt-mapping"></a>Сопоставление SQLAllocStmt
Когда приложение вызывает **SQLAllocStmt** через драйвер ODBC *3. x* , вызов:  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 сопоставляется с **функцию SQLAllocHandle** диспетчером драйверов в драйвере следующим образом:  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 Если для *инпусандле* задано значение *хдбк* , а для *аутпусандлептр* задано значение *фстмт*.
