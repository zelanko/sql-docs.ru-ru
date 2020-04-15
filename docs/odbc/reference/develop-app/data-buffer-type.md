---
title: Тип буфера данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b98ed2ab0865b98884f6dfa1ff20142540ff314
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305250"
---
# <a name="data-buffer-type"></a>Тип буфера данных
Тип буфера данных C указан приложением. С одной переменной это происходит, когда приложение выделяет переменную. С общей памятью - то есть память, указанная указателем пустоты типа - это происходит, когда приложение бросает память к определенному типу. Водитель обнаруживает этот тип двумя способами:  
  
-   **Аргумент типа буфера данных.** Буферы, используемые для передачи значений параметров и данных набора результатов, такие как буфер, связанный с *TargetValuePtr* в **S'LBindCol,** обычно имеют связанный аргумент типа, например аргумент *TargetType* в **S'LBindCol.** В этом аргументе приложение передает идентификатор типа C, соответствующий типу буфера. Например, при следующем вызове на **S'LBindCol**значение SQL_C_TYPE_DATE сообщает водителю, что буфер *Дата* является SQL_DATE_STRUCT:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Для получения дополнительной информации об идентификаторах типов смотрите [типы данных в разделе ODBC,](../../../odbc/reference/develop-app/data-types-in-odbc.md) позже в этом разделе.  
  
-   **Предопределенный тип.** Буферы, используемые для отправки и извлечения опций или атрибутов, таких как буфер, на который указывает аргумент *InfoValuePtr* в **S'LGetInfo,** имеют фиксированный тип, который зависит от указанного варианта. Драйвер предполагает, что буфер данных такого типа; это ответственность приложения за выделение буфера этого типа. Например, при следующем вызове на **s'LGetInfo**драйвер предполагает, что буфер представляет собой 32-битный ряд, потому что это то, что требует SQL_STRING_FUNCTIONS вариант:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Драйвер использует тип данных C для интерпретации данных в буфере.
