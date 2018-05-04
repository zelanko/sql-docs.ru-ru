---
title: Литерал префиксов и суффиксов | Документы Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 435813819f36493b4495786040f4d94d1698a383
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="literal-prefixes-and-suffixes"></a>Литерал префиксов и суффиксов
В инструкции SQL *литерала* является значением фактических данных в символьном представлении. Например в следующей инструкции ABC, FFFF и 10 являются литералами:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Литералы для некоторых типов данных требуют специальных префиксов и суффиксов. В приведенном выше примере символьный литерал (ABC) требуется одинарная кавычка (') в качестве префикса и суффикса, символы 0 x — это префикс, целочисленный литерал (10) не должен иметь префикс или суффикс, требуется двоичный литерал (FFFF).  
  
 Для всех типов данных, за исключением даты, времени и отметок времени, взаимодействующие приложения следует использовать значения, возвращаемые в столбцах LITERAL_PREFIX и LITERAL_SUFFIX в результирующем наборе, созданные **SQLGetTypeInfo**. Для даты, времени, отметки времени и интервала литералами даты и времени взаимодействующие приложения следует использовать escape-последовательности, описанные в предыдущем разделе.
