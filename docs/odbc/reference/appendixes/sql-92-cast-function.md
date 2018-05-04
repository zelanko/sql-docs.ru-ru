---
title: Функции CAST SQL-92 | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce0ff593f8f381efb6d54ea73a8dea04f99823ce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
