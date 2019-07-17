---
title: Длина буфера данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40fe9d23f14d4a7af80fe31a418cccf7133b7252
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067422"
---
# <a name="data-buffer-length"></a>Длина буфера данных
Приложение передает байтовая длина буфера данных драйвера в аргументе, с именем *BufferLength* или таким же именем. Например, в вызове **SQLBindCol**, приложение указывает длину *ValuePtr* буфера (**sizeof (***ValuePtr***)** ):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Драйвер всегда возвращает число байтов, не число символов, в аргументе длина буфера любая функция, которая имеет аргумент строки выходных данных.  
  
 Размеры буферов данных необходимы только для выходных буферов; драйвер использует их, чтобы избежать записи после конца буфера. Тем не менее драйвер проверяет длину буфера данных только в том случае, если буфер содержит данные переменной длины, например символьных или двоичных данных. Если буфер содержит данные фиксированной длины, например структуру целое число или дату драйвер игнорирует длина буфера данных и предполагается, что буфер недостаточно велик для хранения данных. то есть он никогда не усекает данные фиксированной длины. Поэтому очень важно для приложения, чтобы выделить достаточно большой буфер для данных фиксированной длины.  
  
 При выводе строки в усечение данных не происходит (такие как имени курсора, возвращаемого для **SQLGetCursorName**), возвращаемая длина аргумента длина буфера — это максимальное количество символов невозможно.  
  
 Размеры буферов данных не являются обязательными для входные буферы, так как драйвер не записывает эти буферы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование значений длины и индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Длина данных, длина буфера и усечение](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Символьные данные и строки C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
