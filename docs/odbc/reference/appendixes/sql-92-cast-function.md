---
title: "Функции CAST SQL-92 | Документы Microsoft"
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
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8389ff0812c91ca5a35007a21d70a2a1ca0baee8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sql-92-cast-function"></a>Функции CAST SQL-92
**ПРИВЕДЕНИЯ** эквивалентна функции, определенной в SQL-92 **преобразовать** функции, определенной в ODBC. Синтаксис функции, эквивалентные выглядит следующим образом:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL-92 **ПРИВЕДЕНИЯ** функция требует, какие типы данных можно преобразовать в типы данных. (Дополнительные сведения см. в спецификации SQL-92.) **ПРИВЕДЕНИЯ** функция поддерживается на уровне переходные FIPS.  
  
 Приложение может определить поддержку **ПРИВЕДЕНИЯ** работать следующим образом:  
  
1.  Вызовите **SQLGetInfo** с типом SQL_SQL_CONFORMANCE сведения. Если возвращаемое значение для типа данных является SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE или SQL_SC_SQL92_FULL, **ПРИВЕДЕНИЯ** функция поддерживается.  
  
2.  Если возвращаемое значение типа данных SQL_SQL_CONFORMANCE SQL_SC_ENTRY_LEVEL и 0, вызов **SQLGetInfo** с типом SQL_SQL92_VALUE_EXPRESSIONS сведения. Если бита SQL_SVE_CAST **ПРИВЕДЕНИЯ** функция поддерживается.

