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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c8d2d567f899c30dfe91cd35445956cd6214da9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125549"
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
