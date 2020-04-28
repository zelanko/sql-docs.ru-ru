---
title: 'С SQL на C: время | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebd146abf650861099a40bf91b2641df768b343d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296384"
---
# <a name="sql-to-c-time"></a>Преобразование данных из SQL в C: время
Идентификатор для типа данных ODBC SQL:  
  
 SQL_TYPE_TIME  
  
 В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные SQL. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**таржетвалуептр*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* длина байта > символов<br /><br /> *9* <= *BufferLength* <= Длина байтового символа<br /><br /> *BufferLength* < 9|Данные<br /><br /> Усеченные данные [a]<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Длина *BufferLength* > символов<br /><br /> *9* <= *BufferLength* <= длина символов<br /><br /> *BufferLength* < 9|Данные<br /><br /> Усеченные данные [a]<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных в байтах <= *BufferLength*<br /><br /> Длина байта данных > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Нет [b]|Данные|6 [d]|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|Нет [b]|Данные [c]|16 [d]|Недоступно|  
  
 [a] доли секунды времени усекаются.  
  
 [b] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **таржетвалуептр* — это размер типа данных C.  
  
 [c] для полей даты структуры метки времени задана текущая дата, а в поле доли секунды структуры метки времени задано нулевое значение.  
  
 [d] это размер соответствующего типа данных C.  
  
 Когда данные SQL преобразуются в символьные данные C, результирующая строка находится в формате "*чч*:*мм*:*СС*". На этот формат не влияет параметр Windows® Country.
