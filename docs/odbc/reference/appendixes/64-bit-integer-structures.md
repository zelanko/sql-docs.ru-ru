---
title: 64-разрядное целое число структур | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8760b771b4ef44f2728c0947504c46a3f7d28910
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="64-bit-integer-structures"></a>64-разрядное целое число структур
Тип C для SQL_C_SBIGINT и SQL_C_UBIGINT идентификаторы типа данных в компиляторах Microsoft C — _int64. При использовании компилятора, отличного от компилятора Microsoft® C тип C может отличаться. Если компилятор поддерживает 64-битовых целых чисел в собственном коде, драйвера или приложения следует определить ODBCINT64 как тип собственного 64-разрядное целое число. Если компилятор не поддерживает 64-разрядных целых чисел, приложения или драйвера можно определить следующие структуры, чтобы обеспечить доступ к этим данным:  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 Эти структуры должны быть выровнены для 8-байтовой границе, так как 64-разрядное целое число выравнивается по 8-байтовой границе.
