---
title: Функция СЗЛ-92 CAST (англ.) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305065"
---
# <a name="sql-92-cast-function"></a>Функция CAST SQL-92
Функция **CAST,** определяемая в S'L-92, эквивалентна функции **CONVERT,** определенной в ODBC. Синтаксис эквивалентных функций:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Функция S'L-92 **CAST** требует, какие типы данных могут быть преобразованы в другие типы данных. (Для получения более подробной информации см. спецификацию S'L-92.) Функция **CAST** поддерживается на переходном уровне FIPS.  
  
 Приложение может определить поддержку функции **CAST** следующим образом:  
  
1.  Позвоните в **s'LGetInfo** с SQL_SQL_CONFORMANCE типом информации. Если значение возврата для типа информации SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE или SQL_SC_SQL92_FULL, функция **CAST** поддерживается.  
  
2.  Если значение возврата SQL_SQL_CONFORMANCE типа информации составляет SQL_SC_ENTRY_LEVEL или 0, позвоните в **S'LGetInfo** с SQL_SQL92_VALUE_EXPRESSIONS типом информации. Если SQL_SVE_CAST бит установлен, функция **CAST** поддерживается.
