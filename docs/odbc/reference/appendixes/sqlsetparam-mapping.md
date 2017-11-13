---
title: "Сопоставление SQLSetParam | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd23345c0e403e6f4f16419e539c2b5ae277c9d4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

