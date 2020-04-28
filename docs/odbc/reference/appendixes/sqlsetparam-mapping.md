---
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
ms.openlocfilehash: 4d8e632412965664e5cdd9c87dc1e26787dcdab2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300534"
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
