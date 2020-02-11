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
ms.openlocfilehash: 615625ca396e5f2ae094962457cc9e746730ddcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067412"
---
# <a name="data-buffer-type"></a>Тип буфера данных
Тип данных C буфера указывается приложением. В случае с одной переменной это происходит, когда приложение выделяет переменную. С универсальной памятью, то есть память, на которую указывает указатель типа void. это происходит, когда приложение приводит память к определенному типу. Драйвер обнаруживает этот тип двумя способами:  
  
-   **Аргумент типа буфера данных.** Буферы, используемые для перемещения значений параметров и результирующих наборов данных, таких как буфер, привязанный к *таржетвалуептр* в **SQLBindCol**, обычно имеют связанный аргумент типа, например, аргумент *TargetType* в **SQLBindCol**. В этом аргументе приложение передает идентификатор типа C, соответствующий типу буфера. Например, в следующем вызове **SQLBindCol**значение SQL_C_TYPE_DATE сообщает драйверу, что буфер *даты* является SQL_DATE_STRUCTом:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Дополнительные сведения об идентификаторах типов см. в подразделе [типы данных в ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) далее в этом разделе.  
  
-   **Предопределенный тип.** Буферы, используемые для отправки и получения параметров или атрибутов, например буфера, на который указывает аргумент *инфовалуептр* в **SQLGetInfo**, имеют фиксированный тип, зависящий от указанного параметра. Драйвер предполагает, что буфер данных имеет такой тип. за выделение буфера этого типа отвечает приложение. Например, в следующем вызове **SQLGetInfo**драйвер предполагает, что буфер является 32-битным целым числом, так как именно для этого параметра SQL_STRING_FUNCTIONS требуется:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Драйвер использует тип данных C для интерпретации данных в буфере.
