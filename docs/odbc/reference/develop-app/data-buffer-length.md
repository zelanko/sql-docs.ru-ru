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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4a4e9a739201d74cfc6c4f7c18e64b91e0fabe4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305265"
---
# <a name="data-buffer-length"></a>Длина буфера данных
Приложение передает длину байт буфера данных драйверу в аргументе с именем *BufferLength* или аналогичным именем. Например, в следующем вызове **SQLBindCol**приложение задает длину буфера *ValuePtr* (**sizeof (***ValuePtr***)**):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Драйвер всегда будет возвращать число байтов, а не число символов, в аргументе длина буфера любой функции, имеющей аргумент выходной строки.  
  
 Длина буфера данных необходима только для выходных буферов; драйвер использует их, чтобы избежать записи после конца буфера. Однако драйвер проверяет длину буфера данных только в том случае, если буфер содержит данные переменной длины, такие как символьные или двоичные данные. Если буфер содержит данные фиксированной длины, такие как структура типа Integer или Date, драйвер игнорирует длину буфера данных и предполагает, что буфер достаточно велик для хранения данных. то есть он никогда не усекает данные фиксированной длины. Поэтому для приложения важно выделить достаточно большой буфер для данных фиксированной длины.  
  
 При усечении строк, не относящихся к данным (например, имени курсора, возвращаемого для **SQLGetCursorName**), возвращаемая длина в аргументе длины буфера равна максимально допустимой длине символов.  
  
 Размер буфера данных не требуется для входных буферов, так как драйвер не выполняет запись в эти буферы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование значений длины и индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Длина данных, длина буфера и усечение](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Символьные данные и строки C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
