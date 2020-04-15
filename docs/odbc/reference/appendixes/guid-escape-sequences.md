---
title: GUID Побег Последовательности (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44907bfbd884bf361ce5f2ab8b3f6d8a247aba44
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306975"
---
# <a name="guid-escape-sequences"></a>Escape-последовательности GUID
ODBC использует последовательности побега для буквальных GUID. Синтаксис этой последовательности побега заключается в следующем:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Remarks  
 В обозначении BNF синтаксис заключается следующим образом:  
  
 *ODBC-гид-побег* :::  
     *ODBC-эск-инициатор гид* '*гид-значение*' *ODBC-эск-терминатор*  
  
 *ODBC-esc-инициатор* :::  
  
 *ODBC-esc-терминатор* :::  
  
 *guid-значение* ::: *часы-низко-значение guid-сепаратор часы-среднего значения guid-сепаратор часы-высокой стоимости гид-сепаратор часы-seq-значение гид-сепаратор узла-значение*  
  
 *гид-сепаратор* ::  
  
 *часовой низкой стоимости* ::: hex_digit hex_digit hex_digit hex_digit hex_digit *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *часы среднего значения* ::: *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы высокой стоимости* ::: *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы-seq-значение* ::: *hex_digit hex_digit hex_digit hex_digit*  
  
 *-узла значение* ::: hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* ::: 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; &#124; 7 &#124; &#124; 8 &#124; &#124; &#124; B &#124; &#124; D &#124; E &#124; F  
  
 Буквальная последовательность побега GUID поддерживается, если тип данных GUID поддерживается источником данных. Для определения того, поддерживается ли этот тип данных, приложение должно позвонить в **s'LGetTypeInfo.**
