---
title: Данные Буфер Адрес (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578e4e37a78818cb640d9f32e2480cec5951df63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305275"
---
# <a name="data-buffer-address"></a>Адрес буфера данных
Приложение передает адрес буфера данных драйверу в споре, часто названном *ValuePtr* или аналогичном имени. Например, в следующем вызове на **s'LBindCol**приложение указывает адрес переменной *Дата:*  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Как указано в разделе [«Распределение и освобождение буферов»,](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) адрес отложенного буфера должен оставаться в силе до тех пор, пока буфер не будет не связан.  
  
 Если это не запрещено, адрес буфера данных может быть нулевой указатель. Для буферов, используемых для передачи данных водителю, это заставляет водителя игнорировать информацию, обычно содержащуюся в буфере. Для буферов, используемых для получения данных из драйвера, это приводит к тому, что драйвер не возвращает значение. В обоих случаях драйвер игнорирует соответствующий аргумент длины буфера данных.
