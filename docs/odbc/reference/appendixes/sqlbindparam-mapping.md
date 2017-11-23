---
title: "Сопоставление SQLBindParam | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 14af02864d6e0810ffa6ffa49a35bf676c000aea
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlbindparam-mapping"></a>Сопоставление SQLBindParam
**SQLBindParam** действительно невозможен, не рекомендуется из-за не существует в ODBC; Однако он по-прежнему представляет дублированных функций — диспетчер драйверов необходимо экспортировать его, поскольку ISO и откройте группу совместимые приложения будет использовать его. Поскольку **SQLBindParameter** содержит все функциональные возможности **SQLBindParam**, **SQLBindParam** будут сопоставлены на основе **SQLBindParameter** (при базового драйвера ODBC 3*.x* драйвер). ODBC 3*.x* драйвер необходимо реализовать **SQLBindParam**.  
  
## <a name="remarks"></a>Замечания  
 При следующем вызове **SQLBindParam** становится:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 Диспетчер драйверов вызывает **SQLBindParameter** в драйвере следующим образом:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 В разделе [сведения ODBC 64-разрядных](../../../odbc/reference/odbc-64-bit-information.md), если приложение будет выполняться на 64-разрядной операционной системе.  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление нерекомендуемых функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
