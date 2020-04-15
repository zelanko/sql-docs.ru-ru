---
title: 64-Битные структуры с теплом Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ecbe4dae4c1bd21ac3d542ee0d9b18169df0116
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307515"
---
# <a name="64-bit-integer-structures"></a>64-разрядные целочисленные структуры
Тип C для идентификаторов SQL_C_SBIGINT и SQL_C_UBIGINT типа данных в компиляторах Microsoft C является _int64. При использовании компилятора, кроме министера®, тип C может быть другим. Если компилятор поддерживает 64-разрядные ряды на месте, драйвер или приложение должны определить ODBCINT64 как родной 64-битный тип рядов. Если компилятор не поддерживает 64-разрядные ряды на месте, приложение или драйвер может определить следующие структуры, чтобы гарантировать, что он имеет доступ к этим данным:  
  
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
  
 Эти структуры должны быть выровнены с 8-байт границы, потому что 64-битный ряд выравнивается к 8-байт границы.
