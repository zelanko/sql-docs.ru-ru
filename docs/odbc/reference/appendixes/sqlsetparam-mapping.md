---
title: Сопоставление SQLSetParam | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc9d81b92e83f92bb617e004c85fdbc0766de463
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetparam-mapping"></a>Сопоставление SQLSetParam
**SQLSetParam** продолжается для сопоставления на основе **SQLBindParameter** как ODBC 2. *x*. Несмотря на то, что он аналогичен **SQLBindParam**, диспетчер драйверов не соответствует **SQLSetParam** для **SQLBindParam**. Это, поскольку некоторые существующие ODBC 2. *x* драйверы использовать специальное значение *BufferLength* (SQL_SETPARAM_VALUE_MAX), создающий диспетчера драйверов, если он был сопоставлен **SQLSetParam** на основе  **SQLBindParameter** для определения, когда он вызывается по 1. *x* приложений ODBC.  
  
 Вызов  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 приведет к следующим образом:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
