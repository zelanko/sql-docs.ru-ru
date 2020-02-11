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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6682ae98f2da64f6936049bee96fe2fff2a84db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057059"
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
