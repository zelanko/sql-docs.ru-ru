---
title: Сопоставление SQLBindParam | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a2c78cd97b6577be8d11d07325165d6d82cd895
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>См. также  
 [Сопоставление нерекомендуемых функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
