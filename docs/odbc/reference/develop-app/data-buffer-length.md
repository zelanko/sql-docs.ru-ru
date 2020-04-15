---
title: Длина буфера данных Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305265"
---
# <a name="data-buffer-length"></a>Длина буфера данных
Приложение передает длину байт буфера данных водителю в споре, названном *BufferLength* или аналогичным именем. Например, в следующем вызове на **S'LBindCol**приложение определяет длину буфера *ValuePtr* **(размер ***(ValuePtr***)**  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Водитель всегда возвращает количество байтов, а не количество символов, в аргументе длины буфера любой функции, которая имеет аргумент строки вывода.  
  
 Длина буфера данных требуется только для выходных буферов; водитель использует их, чтобы избежать записи мимо конца буфера. Однако водитель проверяет длину буфера данных только тогда, когда буфер содержит данные с переменной длиной, такие как символ или двоичные данные. Если буфер содержит данные с фиксированной длиной, такие как целый ряд или структура даты, драйвер игнорирует длину буфера данных и предполагает, что буфер достаточно велик для хранения данных; то есть, он никогда не усечения фиксированной длины данных. Поэтому для приложения важно выделить достаточно большой буфер для данных с фиксированной длиной.  
  
 При усечении строк вывода, не связанных с данными (например, имя курсора, возвращенное для **S'LGetCursorName),** возвратная длина в аргументе длины буфера является максимально возможной длиной символов.  
  
 Длина буфера данных не требуется для входных буферов, поскольку драйвер не записывает в эти буферы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Использование значений длины/индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Длина данных, длина буфера и усечение](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Символьные данные и строки C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
