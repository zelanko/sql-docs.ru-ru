---
title: Префиксы литералов и суффиксы | Документация Майкрософт
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
ms.openlocfilehash: 56ee50071f622c114bd6d8d04444e78c0fb69d67
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915566"
---
# <a name="literal-prefixes-and-suffixes"></a>Префиксы и суффиксы литералов
В инструкции SQL *литерал* — это символьное представление фактического значения данных. Например, в следующей инструкции ABC, FFFF и 10 являются литералами:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Для литералов некоторых типов данных требуются специальные префиксы и суффиксы. В предыдущем примере символьному литералу (ABC) требуется одиночная кавычка (') в качестве префикса и суффикса, для двоичного литерала (FFFF) требуются символы 0x в качестве префикса, а целочисленный литерал (10) не требует префикса или суффикса.  
  
 Для всех типов данных, кроме даты, времени и меток времени, взаимодействующие приложения должны использовать значения, возвращаемые в столбцах LITERAL_PREFIX и LITERAL_SUFFIX в результирующем наборе, созданном **SQLGetTypeInfo**. Для литеральных литералов даты, времени, timestamp и DateTime в взаимодействующих приложениях следует использовать escape-последовательности, описанные в предыдущем разделе.
