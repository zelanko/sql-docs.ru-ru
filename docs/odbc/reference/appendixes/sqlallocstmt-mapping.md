---
description: Сопоставление SQLAllocStmt
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
ms.openlocfilehash: e8307dce9e95c98ff92912517d5b574883d6298c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424926"
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
