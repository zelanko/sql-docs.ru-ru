---
description: Сопоставление SQLSetParam
title: Сопоставление SQLSetParam | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2c16f942920b5fefff664cc647f4edfc9ab6d13
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339300"
---
# <a name="sqlsetparam-mapping"></a>Сопоставление SQLSetParam
**SQLSetParam** по **SQLBindParameter** , как в ODBC 2, будет продолжать сопоставляться. *x*. Несмотря на то, что концептуально похоже на **склбиндпарам**, диспетчер драйверов не сопоставляет **SQLSetParam** с **склбиндпарам**. Это связано с тем, что некоторые существующие ODBC 2. драйверы *x* используют специальное значение *BufferLength* (SQL_SETPARAM_VALUE_MAX), которое диспетчер драйверов создает при сопоставлении **SQLSetParam** поверх **SQLBindParameter** , чтобы определить, когда он вызывается с помощью 1. Приложение *x* ODBC.  
  
 Вызов метода  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 приведет к следующему результату:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
