---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d282798a31ac9059ed3c1901ea01f1f3104f09c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056882"
---
# <a name="sql-to-c-date"></a>SQL в C: Date
Идентификатор для типа данных ODBC SQL дата является:  
  
 SQL_TYPE_DATE  
  
 Следующая таблица показывает ODBC C типы данных, к которым можно преобразовать даты данных SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов<br /><br /> 11 < = *BufferLength* < = байтов символов<br /><br /> *BufferLength* < 11|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|10<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной<br /><br /> 11 < = *BufferLength* < = символов<br /><br /> *BufferLength* < 11|Data<br /><br /> Усеченные данные<br /><br /> Не определено.|10<br /><br /> Длина данных в символах<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Data<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Нет [a]|Data|6 [c]|Н/Д|  
|SQL_C_TYPE_TIMESTAMP|Нет [a]|Данные [b]|16 [c]|Н/Д|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] поля времени структура отметки времени присваивается нулевое значение.  
  
 [c] это размер соответствующего типа данных C.  
  
 При преобразовании даты данных SQL в символьный C результирующая строка находится в "*гггг*-*мм*-*дд*" формат. Этот формат не влияют параметры Windows® страны.
