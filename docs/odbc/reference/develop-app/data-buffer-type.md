---
title: Тип буфера данных | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e02d42d6d63608ccb70dc984e05ae11578d3160
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049970"
---
# <a name="data-buffer-type"></a>Тип буфера данных
Тип данных C буфера указан приложением. С одной переменной это происходит, когда приложение выделяет переменную. С универсального память — то есть памяти, на который ссылается указатель типа void - это происходит, когда приложение приводит к памяти для определенного типа. Драйвер обнаруживает этот тип одним из двух способов:  
  
-   **Аргумент типа буфера данных.** Буферов, используемых для передачи значений параметров и результирующий набор данных, такие как буфер привязан к *TargetValuePtr* в **SQLBindCol**, обычно имеют связанный тип аргумента, такие как  *TargetType* аргумента в **SQLBindCol**. В этом аргументе приложение передает идентификатор типа C, соответствующий типу буфера. Например, в вызове **SQLBindCol**, значение SQL_C_TYPE_DATE сообщает драйверу, что *даты* буфер является SQL_DATE_STRUCT:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Дополнительные сведения об идентификаторах типа см. в разделе [типы данных в ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) разделе далее в этом разделе.  
  
-   **Предопределенный тип.** Буферов, используемых для отправки и получения параметров или атрибуты, такие как буфер, на которые указывают *InfoValuePtr* аргумента в **SQLGetInfo**, имеют фиксированный тип, который зависит от указанных параметрах. Драйвер предполагает, что буфер данных этого типа; приложения отвечает выделить буфер данного типа. Например, в вызове **SQLGetInfo**, драйвер предполагает буфер является 32-разрядное целое число, поскольку это требует параметр SQL_STRING_FUNCTIONS:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Драйвер использует тип данных C для интерпретации данных в буфере.
