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
ms.openlocfilehash: 26f9bdc0564b98132bb5ec413c99917e78e4d62e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855182"
---
# <a name="sqlbindparam-mapping"></a>Сопоставление SQLBindParam
**SQLBindParam** не может по-настоящему вызываться не рекомендуется так как не существует в ODBC; тем не менее, оно по-прежнему представляет продублированные функции — диспетчер драйверов необходимо экспортировать его, поскольку ISO и откройте совместимого группы приложений будут использовать его. Так как **SQLBindParameter** содержит все функциональные возможности **SQLBindParam**, **SQLBindParam** будет сопоставляться на основе **SQLBindParameter** (при базового драйвера ODBC 3 *.x* драйвер). ODBC 3 *.x* драйвер не нужно реализовать **SQLBindParam**.  
  
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
