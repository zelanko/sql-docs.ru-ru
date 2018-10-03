---
title: Функции CAST SQL-92 | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db5077b9df2673593b6eaec9622aafd1d2c77234
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753992"
---
# <a name="sql-92-cast-function"></a>Функция CAST SQL-92
**ПРИВЕДЕНИЯ** эквивалентна функции, определенной в SQL-92 **преобразовать** функции, определенной в ODBC. Синтаксис эквивалентные функции выглядит следующим образом:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL-92 **ПРИВЕДЕНИЯ** функция задает, какие типы данных можно преобразовать в какие другие типы данных. (Дополнительные сведения см. в спецификации SQL-92). **ПРИВЕДЕНИЯ** функция поддерживается на уровне FIPS Transitional.  
  
 Приложение может определить поддержку **ПРИВЕДЕНИЯ** функцию следующим образом:  
  
1.  Вызовите **SQLGetInfo** с типом SQL_SQL_CONFORMANCE сведения. Если возвращаемое значение для типа данных является SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE или SQL_SC_SQL92_FULL, **ПРИВЕДЕНИЯ** функция поддерживается.  
  
2.  Если возвращаемое значение типа сведения SQL_SQL_CONFORMANCE SQL_SC_ENTRY_LEVEL или 0, вызов **SQLGetInfo** с типом SQL_SQL92_VALUE_EXPRESSIONS сведения. Если бита SQL_SVE_CAST **ПРИВЕДЕНИЯ** функция поддерживается.
