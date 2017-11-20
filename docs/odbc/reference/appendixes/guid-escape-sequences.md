---
title: "Идентификатор GUID Escape-последовательности | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d4ed6e517d9a8fa6f4c28c7b05541d36262df2a8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="guid-escape-sequences"></a>Идентификатор GUID Escape-последовательности
ODBC использует escape-последовательности для литералов GUID. Ниже приведен синтаксис escape-последовательности:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Замечания  
 В форме БЭКУСА-Наура используется следующий синтаксис:  
  
 *ODBC guid-escape* :: =  
     *ODBC-esc инициатор guid* "*значение идентификатора guid*" *ODBC esc признака конца.*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC esc признак конца* :: =}  
  
 *значение идентификатора GUID* :: = *часы низкой стоимости guid разделитель часов среднего значения guid разделитель часов высокой ценности guid разделитель часов seq значений guid разделитель значение узла*  
  
 *GUID разделитель* :: = -  
  
 *часы низкой стоимости* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *часы среднего значения* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы высокой ценности* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы seq значение* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *значение для узла часы* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; Б &#124; И &#124; Д &#124; В &#124; F  
  
 Литерал escape-последовательность GUID поддерживается в том случае, если тип данных GUID поддерживается источником данных. Приложение должно вызывать **SQLGetTypeInfo** для определения, является ли этот тип данных поддерживается.

