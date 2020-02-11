---
title: Сопоставление Склбиндпарам | Документация Майкрософт
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
ms.openlocfilehash: ecec6116ee16f4affa615518a690d2c665648464
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091239"
---
# <a name="sqlbindparam-mapping"></a>Сопоставление SQLBindParam
**Склбиндпарам** нельзя выключать как устаревший, так как он никогда не СУЩЕСТВОВАЛ в ODBC; Однако он по-прежнему представляет собой дублирующуюся функциональность. диспетчеру драйверов необходимо экспортировать его, так как ISO и открытые приложения, соответствующие группам, будут использовать его. Поскольку **SQLBindParameter** содержит все функции **склбиндпарам**, **Склбиндпарам** будет сопоставляться с **SQLBindParameter** (если базовый драйвер является драйвером ODBC *3. x* ). Драйверу ODBC *3. x* не требуется реализовывать **склбиндпарам**.  
  
## <a name="remarks"></a>Remarks  
 При следующем вызове **склбиндпарам** :  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 Диспетчер драйверов вызывает **SQLBindParameter** в драйвере следующим образом:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Если приложение будет работать в 64-разрядной операционной системе, см. [сведения о ODBC 64-bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление нерекомендуемых функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
