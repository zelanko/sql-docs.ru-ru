---
title: 'SQL в C: Двоичный | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16112ca3b66e0218efd54d3bf385e04cb654e3e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270962"
---
# <a name="sql-to-c-binary"></a>SQL в C: Бинарный
Идентификаторы для двоичных типов данных ODBC SQL — это:  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 Следующая таблица показывает ODBC C типы данных, к которым могут преобразовываться двоичных данных SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Длину в байтах данных) \* 2 < *BufferLength*<br /><br /> (Длину в байтах данных) \* 2 > = *BufferLength*|Данные<br /><br /> Усеченные данные|Длина данных в байтах<br /><br /> Длина данных в байтах|н/д<br /><br /> 01004|  
|SQL_C_WCHAR|(Символьную длину данных) \* 2 < *BufferLength*<br /><br /> (Символьную длину данных) \* 2 > = *BufferLength*|Данные<br /><br /> Усеченные данные|Длина данных в символах<br /><br /> Длина данных в символах|н/д<br /><br /> 01004|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Длину данных в байтах > *BufferLength*|Данные<br /><br /> Усеченные данные|Длина данных в байтах<br /><br /> Длина данных в байтах|н/д<br /><br /> 01004|  
  
 При преобразовании в символьный C двоичных данных SQL каждый байт (8 бит), источник данных представляется как два символа ASCII. Эти символы имеются представление символа ASCII числа в его в шестнадцатеричной форме. Например двоичные 00000001 преобразуется в «01» и двоичное 11111111 преобразуется в «FF».  
  
 Драйвер всегда преобразует отдельных байтов пар шестнадцатеричных цифр и завершает символьной строки с нулевым байтом. Из-за этого Если *BufferLength* четное, и меньше, чем длина преобразованных данных, последний байт **TargetValuePtr* буфер не используется. (Преобразованных данных требует четное число байтов, следующего за последним байтов является нулевым байтом и последний байт не может использоваться.)  
  
> [!NOTE]  
>  Разработчикам приложений не рекомендуется привязка двоичных данных SQL в символьный тип данных C. Это преобразование обычно является неэффективным и медленно.
