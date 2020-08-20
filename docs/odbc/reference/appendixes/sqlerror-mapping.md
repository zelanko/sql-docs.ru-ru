---
description: Сопоставление SQLError
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d18d1b25acbbe56f29555274a7b8d995b7355d0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466026"
---
# <a name="sqlerror-mapping"></a>Сопоставление SQLError
Когда приложение вызывает **SqlError** через драйвер ODBC *3. x* , вызов метода  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 сопоставлен с  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 Если для аргумента *параметром handletype* задано значение SQL_HANDLE_ENV, SQL_HANDLE_DBC или SQL_HANDLE_STMT, соответственно, и аргумент *Handle* имеет значение в *хенв*, *хдбк*или *хстмт*, в зависимости от ситуации. Аргумент *рекнумбер* определяется диспетчером драйверов.
