---
title: "Литерал префиксов и суффиксов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f702ed5210b5735a0d3dac418f8296ce274a729b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="literal-prefixes-and-suffixes"></a>Литерал префиксов и суффиксов
В инструкции SQL *литерала* является значением фактических данных в символьном представлении. Например в следующей инструкции ABC, FFFF и 10 являются литералами:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Литералы для некоторых типов данных требуют специальных префиксов и суффиксов. В приведенном выше примере символьный литерал (ABC) требуется одинарная кавычка (') в качестве префикса и суффикса, символы 0 x — это префикс, целочисленный литерал (10) не должен иметь префикс или суффикс, требуется двоичный литерал (FFFF).  
  
 Для всех типов данных, за исключением даты, времени и отметок времени, взаимодействующие приложения следует использовать значения, возвращаемые в столбцах LITERAL_PREFIX и LITERAL_SUFFIX в результирующем наборе, созданные **SQLGetTypeInfo**. Для даты, времени, отметки времени и интервала литералами даты и времени взаимодействующие приложения следует использовать escape-последовательности, описанные в предыдущем разделе.
