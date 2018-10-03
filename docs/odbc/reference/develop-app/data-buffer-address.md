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
manager: craigg
ms.openlocfilehash: f07f835361fcf29143376fe468a55f0bf26e31e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601282"
---
# <a name="data-buffer-address"></a>Адрес буфера данных
Приложение передает адрес буфера данных драйвера в аргументе, часто с именем *ValuePtr* или таким же именем. Например, в вызове **SQLBindCol**, приложение указывает адрес *даты* переменной:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Как упоминалось в [распределение и освобождение буферов](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) разделе адрес отложенного буфера должен оставаться действительным, пока буфер не связан.  
  
 Если он запрещен в частности, адрес буфера данных может быть пустым указателем. Для буферов, используемых для отправки данных в драйвер в результате драйвер пропустили информацию, обычно содержащихся в буфере. Для буферов, используемых для получения данных от драйвера в результате драйвер не будет возвращать значение. В обоих случаях драйвер пропускает соответствующего аргумента длина буфера данных.
