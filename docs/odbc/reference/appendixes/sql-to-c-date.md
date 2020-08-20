---
description: 'Преобразование данных из SQL в C: даты'
title: 'SQL в C: Дата | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5bab301c7a4bc55289006df1c9df5498629f317
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456520"
---
# <a name="sql-to-c-date"></a>Преобразование данных из SQL в C: даты
Идентификатор для типа данных ODBC SQL:  
  
 SQL_TYPE_DATE  
  
 В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные SQL. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**таржетвалуептр*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* длина байта > символов<br /><br /> 11 <= *BufferLength* <= Длина байтового символа<br /><br /> *BufferLength* < 11|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|10<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина *BufferLength* > символов<br /><br /> 11 <= *BufferLength* <= длина символа<br /><br /> *BufferLength* < 11|Данные<br /><br /> Усеченные данные<br /><br /> Не определено.|10<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных в байтах <= *BufferLength*<br /><br /> Длина байта данных > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Нет [a]|Данные|6 [c]|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|Нет [a]|Данные [b]|16 [c]|Недоступно|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **таржетвалуептр* — это размер типа данных C.  
  
 [b] поля времени структуры метки времени имеют нулевое значение.  
  
 [c] это размер соответствующего типа данных C.  
  
 Когда дата SQL преобразуется в символьные данные C, результирующая строка находится в формате "*гггг* - *мм* - *дд*". На этот формат не влияет параметр Windows® Country.
