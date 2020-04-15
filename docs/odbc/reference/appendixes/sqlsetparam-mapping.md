---
title: Картирование СЗЛСЕтПарам (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d8e632412965664e5cdd9c87dc1e26787dcdab2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300534"
---
# <a name="sqlsetparam-mapping"></a>Сопоставление SQLSetParam
**В** верхней части **S'LBindParameter,** как и в ODBC 2, по-прежнему отображается карта. *x*. Несмотря на то, что он концептуально похож на **S'LBindParam,** менеджер драйверов не отображает **s'LSetParam** на **S'LBindParam.** Это потому, что некоторые существующие ODBC 2. *драйверы x* используют специальное значение *BufferLength* (SQL_SETPARAM_VALUE_MAX), которое генерирует менеджер драйверов, когда он отображает **S'LSetParam** поверх **S'LBindParameter,** чтобы определить, когда он вызывается 1. *приложение x* ODBC.  
  
 Звонок в  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 приведет к следующему:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
