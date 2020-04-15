---
title: СЗЛБиндпарам Картирование (ru) Документы Майкрософт
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
ms.openlocfilehash: c1df595722297c91dc75398470912188e109e278
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305444"
---
# <a name="sqlbindparam-mapping"></a>Сопоставление SQLBindParam
**S'LBindParam** действительно не может быть назван обесценилась, потому что он никогда не был там, в ODBC; однако он по-прежнему представляет дублированную функциональность - менеджер драйверов должен экспортировать ее, потому что iSO и приложения, соответствующие требованиям Open Group, будут использовать его. В связи с тем, что **S'LBindParameter** содержит всю функциональность **S'LBindParam,** **S'LBindParam** будет отображаться поверх **S'LBindParameter** (когда базовым драйвером является драйвер ODBC *3.x).* Драйвер ODBC *3.x* не нуждается в **реализации S'LBindParam.**  
  
## <a name="remarks"></a>Remarks  
 При следующем звонке в **S'LBindParam:**  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 Менеджер драйвера вызывает **S'LBindParameter** в драйвере следующим образом:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Смотрите [информацию ODBC 64-Bit,](../../../odbc/reference/odbc-64-bit-information.md)если ваше приложение будет работать на 64-битной операционной системе.  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление нерекомендуемых функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
