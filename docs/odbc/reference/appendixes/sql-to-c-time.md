---
title: 'SQL в C: Время | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 99f8219ef53f72b0d7ab1477bba5d24d441a3141
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065082"
---
# <a name="sql-to-c-time"></a>SQL в C: Time
Идентификатор для времени, которое имеет тип данных ODBC SQL:  
  
 SQL_TYPE_TIME  
  
 Ниже приведены ODBC C типы данных, к которым время SQL данные могут преобразовываться. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов<br /><br /> *9* <= *BufferLength* < = байтов символов<br /><br /> *BufferLength* < 9|Data<br /><br /> Усеченные данные [a]<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной<br /><br /> *9* <= *BufferLength* < = символов<br /><br /> *BufferLength* < 9|Data<br /><br /> Усеченные данные [a]<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Н/Д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Data<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Нет [b]|Data|6 [d]|Н/Д|  
|SQL_C_TYPE_TIMESTAMP|Нет [b]|Данные [c]|16 [d]|Н/Д|  
  
 [a] время на доли секунды усекаются.  
  
 [b] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [c поля даты структура отметки времени задаются до текущей даты, а в поле долей секунд структура отметки времени, равным нулю.  
  
 [d] это размер соответствующего типа данных C.  
  
 При преобразовании данных SQL времени в символьный C результирующая строка находится в "*hh*:*мм*:*ss*" формат. Этот формат не влияют параметры Windows® страны.
