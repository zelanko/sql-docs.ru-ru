---
title: Escape-последовательности даты, времени и метки времени | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC]
ms.assetid: 67b7dee0-e5b1-4469-a626-0c7767852b80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6cbcdac00b4cd7497f53c9f3a13f4f7303b5154
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284346"
---
# <a name="date-time-and-timestamp-escape-sequences"></a>Escape-последовательности для значений даты, времени и отметок времени
ODBC определяет escape-последовательности для литералов даты, времени и меток времени. Синтаксис этих escape-последовательностей выглядит следующим образом:  
  
```  
  
{d 'value'}  
{t 'value'}  
{ts 'value'}  
```  
  
 В нотации BNF синтаксис выглядит следующим образом:  
  
```  
  
      ODBC-date-time-escape ::=  
     ODBC-date-escape  
     | ODBC-time-escape  
     | ODBC-timestamp-escapeODBC-date-escape ::=  
     ODBC-esc-initiator d 'date-value' ODBC-esc-terminatorODBC-time-escape ::=  
     ODBC-esc-initiator t 'time-value' ODBC-esc-terminatorODBC-timestamp-escape ::=  
     ODBC-esc-initiator ts 'timestamp-value' ODBC-esc-terminatorODBC-esc-initiator ::= {  
ODBC-esc-terminator ::= }  
date-value ::=   
     years-value date-separator months-value date-separator days-valuetime-value ::=   
     hours-value time-separator minutes-value time-separatorseconds-valuetimestamp-value ::= date-value timestamp-separator time-valuedate-separator ::= -  
time-separator ::= :  
timestamp-separator ::=  
     (The blank character)years-value ::= digit digit digit digitmonths-value ::= digit digitdays-value ::= digit digithours-value ::= digit digitminutes-value ::= digit digitseconds-value ::= digit digit[.digit...]  
```  
  
## <a name="remarks"></a>Remarks  
 Escape-последовательности литералов даты, времени и отметок времени поддерживаются, если источник данных поддерживает типы данных даты, времени и отметки времени. Приложение должно вызывать **SQLGetTypeInfo** , чтобы определить, поддерживаются ли эти типы данных.
