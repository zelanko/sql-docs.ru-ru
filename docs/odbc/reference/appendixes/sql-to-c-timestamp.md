---
title: 'SQL в C: Метка времени | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69c9f1258f35a69d6554783f5d1b4ca79be313d2
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2019
ms.locfileid: "54419959"
---
# <a name="sql-to-c-timestamp"></a>SQL в C: Отметка времени

Идентификатор для типа данных ODBC SQL timestamp выглядит так:

- SQL_TYPE_TIMESTAMP  

Следующая таблица показывает ODBC C типы данных, к которым timestamp SQL данные могут быть преобразованы. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов<br /><br /> 20 < = *BufferLength* < = байтов символов<br /><br /> *BufferLength* < 20|Данные<br /><br /> Усеченные данные [b]<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной<br /><br /> 20 < = *BufferLength* < = символов<br /><br /> *BufferLength* < 20|Данные<br /><br /> Усеченные данные [b]<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|н/д<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Часть времени для отметки времени равна нулю [a]<br /><br /> Метки времени — времени ненулевое значение [a]|Данные<br /><br /> Усеченные данные [c]|6 [f]<br /><br /> 6 [f]|н/д<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Метки времени с обозначением долей секунды равно нулю [a]<br /><br /> Метки времени с обозначением долей секунды является ненулевое значение [a]|Данные [d]<br /><br /> Усеченные данные [d], [e]|6 [f]<br /><br /> 6 [f]|н/д<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|Метки времени с обозначением долей секунды не усекается, [a]<br /><br /> Усекается с обозначением долей секунды из метки времени [a]|Данные [e]<br /><br /> Усеченные данные [e]|16 [f]<br /><br /> 16 [f]|н/д<br /><br /> 01S07|  

 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] метка времени на доли секунды усекаются.  
  
 [c время отметки времени округляются.  
  
 [d] в части даты отметки времени учитывается.  
  
 [e] с обозначением долей секунды отметки времени усекается.  
  
 [f] это размер соответствующего типа данных C.  

При преобразовании в символьный C данных timestamp SQL результирующая строка находится в "*гггг*-*мм*-*дд* *чч* :*мм*:*ss*[.*f...*]» формат, где можно использовать до девяти цифр для долей секунды. Этот формат не влияют параметры Windows® страны. (За исключением десятичного разделителя и доли секунды, весь формата необходимо использовать, независимо от того, точность типа данных timestamp SQL.)
