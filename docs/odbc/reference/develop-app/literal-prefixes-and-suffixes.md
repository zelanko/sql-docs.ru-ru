---
title: Буквальные префиксы и суффиксы Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d52ca54c329353e3d9dc67ca35d89b2d28cedf74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287986"
---
# <a name="literal-prefixes-and-suffixes"></a>Префиксы и суффиксы литералов
В заявлении, представленном в отчете S'L, *буквально* является представление символов фактического значения данных. Например, в следующем заявлении, ABC, FFFF, и 10 являются буквальными:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Для некоторых типов данных требуются специальные префиксы и суффиксы. В предыдущем примере персонаж буквально (ABC) требует одной отметки цитаты (') как приставку и суффикс, двоичный буквальный (FFFF) требует символов 0x в качестве префикса, а целый буквальный (10) не требует префикса или суффикса.  
  
 Для всех типов данных, за исключением даты, времени и меток времени, совместимые приложения должны использовать значения, возвращенные в LITERAL_PREFIX и LITERAL_SUFFIX столбцов в наборе результатов, созданных **S'LGetTypeInfo.** Для даты, времени, метки времени и интервала времени даты буквальных, совместимые приложения должны использовать последовательности побега, обсуждаемые в предыдущем разделе.
