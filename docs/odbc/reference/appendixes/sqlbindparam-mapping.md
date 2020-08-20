---
description: Сопоставление SQLBindParam
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f998fd30716e479cb4dd0650af53c5a24483f2f5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456465"
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
