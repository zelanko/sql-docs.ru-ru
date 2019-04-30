---
title: Сопоставление SQLBindParam | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57e0fe66d76f91c8cea35710e9d0245db7619628
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199711"
---
# <a name="sqlbindparam-mapping"></a>Сопоставление SQLBindParam
**SQLBindParam** не может по-настоящему вызываться не рекомендуется, так как он не существует в ODBC; тем не менее, он по-прежнему представляет продублированные функции — диспетчер драйверов необходимо экспортировать его, поскольку ISO и откройте группу совместимые приложения будет использовать его. Так как **SQLBindParameter** содержит все функциональные возможности **SQLBindParam**, **SQLBindParam** будет сопоставляться на основе **SQLBindParameter** (при базового драйвера ODBC 3 *.x* драйвер). ODBC 3 *.x* драйвер не нужно реализовать **SQLBindParam**.  
  
## <a name="remarks"></a>Примечания  
 Если следующий вызов **SQLBindParam** выполняется:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 Диспетчер драйверов вызывает **SQLBindParameter** в драйвере следующим образом:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 См. в разделе [сведения о ODBC 64-разрядном](../../../odbc/reference/odbc-64-bit-information.md), если приложение выполняется в 64-разрядной операционной системе.  
  
## <a name="see-also"></a>См. также  
 [Сопоставление нерекомендуемых функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
