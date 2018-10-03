---
title: Префиксы и суффиксы литералов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4eabc3e0c354e02ad8df790d896dc43ae49c9bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680862"
---
# <a name="literal-prefixes-and-suffixes"></a>Префиксы и суффиксы литералов
В инструкции SQL *литерала* является представлением символа конкретного значения. Например в следующей инструкции, ABC "," FFFF "и" 10 являются литералами:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Литералы для некоторых типов данных требуют специальных префиксы и суффиксы. В приведенном выше примере символьный литерал ("ABC") требуется знак одинарной кавычки (') в качестве префикса и суффикса, Двоичный литерал (FFFF) требует символы 0 x в качестве префикса и целочисленный литерал (10) не требует префикса или суффикса.  
  
 Для всех типов данных, за исключением даты, времени и отметок времени, с возможностью взаимодействия приложения должны использовать значения, возвращаемые в столбцах LITERAL_PREFIX и LITERAL_SUFFIX в результирующем наборе, созданные **SQLGetTypeInfo**. Для даты, времени, timestamp и интервал литералами даты и времени взаимодействующие приложения следует использовать escape-последовательности, описанных в предыдущем разделе.
