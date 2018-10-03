---
title: Date, Time и Timestamp escape-последовательности | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9131e5fa8f16a137461bde5ecea3fd793b2cf9be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792712"
---
# <a name="date-time-and-timestamp-escape-sequences"></a>Escape-последовательности для значений даты, времени и отметок времени
ODBC определяет управляющие последовательности для даты, времени и литералы отметки времени. Ниже приведен синтаксис escape-последовательности:  
  
```  
  
{d 'value'}  
{t 'value'}  
{ts 'value'}  
```  
  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
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
  
## <a name="remarks"></a>Примечания  
 Литерал escape-последовательности, date, time и timestamp поддерживаются в том случае, если типы данных date, time и timestamp поддерживаются источником данных. Приложение должно вызывать **SQLGetTypeInfo** чтобы определить, поддерживаются ли эти типы данных.
