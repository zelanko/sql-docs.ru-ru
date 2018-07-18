---
title: Длины буфера данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b40fb1b58a10ddd5db371869584b4d29f2110855
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910209"
---
# <a name="data-buffer-length"></a>Длина буфера данных
Приложение передает байтовая длина буфера данных к драйверу в аргумент с именем *BufferLength* или же именем. Например, в вызове **SQLBindCol**, приложение указывает длину *ValuePtr* буфера (**sizeof (***ValuePtr***)**):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Драйвер всегда возвращает количество байтов, а не количество символов, в качестве аргумента длина буфера функций любая функция, которая имеет аргумент строки выходных данных.  
  
 Размеры буферов данных требуются только для выходных буферов; драйвер использует их во избежание записи после конца буфера. Тем не менее драйвер проверяет длину буфера данных только в том случае, когда буфер содержит данные переменной длины, например символьных или двоичных данных. Если буфер содержит данные фиксированной длины, например целое число или дату структуры, драйвер пропускает размера буфера данных и предполагается, что буфер достаточно велик для хранения данных; то есть он никогда не усекает данные фиксированной длины. Поэтому очень важно для приложения, чтобы выделить достаточно большого размера буфера для данных фиксированной длины.  
  
 При выводе строки в усечение данных не происходит (такие как имя курсора возвращается для **SQLGetCursorName**), возвращаемая длина аргумента длина буфера — это максимальное количество символов возможно.  
  
 Размеры буферов данных не требуются для входные буферы, так как драйвер не записывает эти буферы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование значений длины/индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Длина данных, длина буфера и усечение](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Символьные данные и строки C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
