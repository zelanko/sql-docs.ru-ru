---
description: Escape-последовательности GUID
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7babe2d26c0e5f2b311f8df5bbd1763622f3042
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466160"
---
# <a name="guid-escape-sequences"></a>Escape-последовательности GUID
ODBC использует escape-последовательности для литералов GUID. Синтаксис этой escape-последовательности выглядит следующим образом:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Комментарии  
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
