---
title: Escape-последовательности GUID | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a74ed9d4dfe0afb8bf59abb11220a0677d000bfb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947586"
---
# <a name="guid-escape-sequences"></a>Escape-последовательности GUID
ODBC использует escape-последовательности для литералов GUID. Синтаксис этой escape-последовательности выглядит следующим образом:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Remarks  
 В нотации BNF синтаксис выглядит следующим образом:  
  
 *ODBC-GUID-escape* :: =  
     *ODBC-ESC-идентификатор GUID инициатора* "*GUID-value*" *ODBC-ESC-признак конца*  
  
 *ODBC-ESC-инициатор* :: = {  
  
 *ODBC-ESC-признак конца* :: =}  
  
 *GUID-value* :: = *таймер — минимальное значение GUID-разделитель — часы среднего* значения с разделителями-запятыми-значение GUID-разделитель "часы — последовательность-значение GUID-разделитель"  
  
 *GUID-separator* :: =-  
  
 *Clock-низкое значение* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *Clock-средняя-значение* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы-высокое значение* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *Clock-seq-value* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы-node-значение* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 Escape-последовательность литерала GUID поддерживается, если тип данных GUID поддерживается источником данных. Приложение должно вызвать **SQLGetTypeInfo** , чтобы определить, поддерживается ли этот тип данных.
