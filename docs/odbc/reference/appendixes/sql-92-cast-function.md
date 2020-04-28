---
title: Функция CAST SQL-92 | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09d2a2de710dafd4e744166c4219f4c903fd3321
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305065"
---
# <a name="sql-92-cast-function"></a>Функция CAST SQL-92
Функция **Cast** , определенная в SQL-92, эквивалентна функции **Convert** , определенной в ODBC. Синтаксис эквивалентных функций выглядит следующим образом:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Функция **Cast** SQL-92 позволяет указать, какие типы данных можно преобразовать в другие типы данных. (Дополнительные сведения см. в спецификации SQL-92.) Функция **Cast** поддерживается на уровне переходов FIPS.  
  
 Приложение может определить поддержку функции **Cast** следующим образом:  
  
1.  Вызовите **SQLGetInfo** с типом сведений SQL_SQL_CONFORMANCE. Если возвращаемое значение для типа сведений — SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE или SQL_SC_SQL92_FULL, функция **Cast** поддерживается.  
  
2.  Если возвращаемое значение типа данных SQL_SQL_CONFORMANCE равно SQL_SC_ENTRY_LEVEL или 0, вызовите **SQLGetInfo** с типом сведений SQL_SQL92_VALUE_EXPRESSIONS. Если задан бит SQL_SVE_CAST, функция **Cast** поддерживается.
