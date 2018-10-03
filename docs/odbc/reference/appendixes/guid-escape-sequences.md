---
title: Идентификатор GUID escape-последовательности | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: bf41671abc6393a18fad06e1debd297fed1f04c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654987"
---
# <a name="guid-escape-sequences"></a>Escape-последовательности GUID
ODBC использует escape-последовательности для литералов GUID. Синтаксис escape-последовательность выглядит следующим образом:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Примечания  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *Guid-escape-последовательность ODBC* :: =  
     *ODBC-esc инициатор guid* "*значение идентификатора guid*" *ODBC esc признак конца.*  
  
 *ODBC-esc инициатор* :: = {}  
  
 *ODBC-esc-признак конца* :: =}  
  
 *значение идентификатора GUID* :: = *часы низкой стоимости guid разделитель часов среднего значения guid разделитель часов высокой ценности guid разделитель часов seq значение guid разделитель значение узла*  
  
 *GUID разделитель* :: = -  
  
 *часы низкой стоимости* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *показания часов среднего* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *часы высокой ценности* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *seq показания часов* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *значение для узла часы* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; объект &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 Литерал escape-последовательности GUID поддерживается в том случае, если типом данных GUID поддерживается источником данных. Приложение должно вызывать **SQLGetTypeInfo** чтобы определить, поддерживается ли этот тип данных.
