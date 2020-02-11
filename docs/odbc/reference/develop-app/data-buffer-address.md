---
title: Адрес буфера данных | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7cd157edd6111dec29ae238a1c383879e66ac0b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067430"
---
# <a name="data-buffer-address"></a>Адрес буфера данных
Приложение передает адрес буфера данных драйверу в аргументе, который часто называется *ValuePtr* или аналогичным именем. Например, в следующем вызове **SQLBindCol**приложение указывает адрес переменной *даты* :  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Как упоминалось в разделе [выделение и освобождение буферов](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) , адрес отложенного буфера должен оставаться действительным до тех пор, пока не будет отменена привязка буфера.  
  
 Если это не запрещено специально, адрес буфера данных может быть пустым указателем. Для буферов, используемых для отправки данных драйверу, это приводит к тому, что драйвер игнорирует информацию, которая обычно содержится в буфере. Для буферов, используемых для получения данных из драйвера, это приводит к тому, что драйвер не возвращает значение. В обоих случаях драйвер игнорирует соответствующий аргумент длины буфера данных.
