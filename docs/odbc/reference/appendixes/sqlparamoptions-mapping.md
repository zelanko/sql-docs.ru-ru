---
title: Сопоставление SQLParamOptions | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLParamOptions
- SQLParamOptions function [ODBC], mapping
ms.assetid: 57ed65f6-9620-4738-b331-19d2a2b5cae4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7f4fa71c06b4a9bf3b01d39fa02d4eadeb9b0778
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125719"
---
# <a name="sqlparamoptions-mapping"></a>Сопоставление SQLParamOptions
Если приложение вызывает **SQLParamOptions** через ODBC *3.x* драйвера, вызов метода  
  
```  
SQLParamOptions(hstmt, crow, piRow);  
```  
  
 будет сопоставлен с двумя вызовов **SQLSetStmtAttr** следующим образом:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);  
```
