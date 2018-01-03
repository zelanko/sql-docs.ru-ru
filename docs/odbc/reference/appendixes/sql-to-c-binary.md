---
title: "SQL в двоичное C: | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 293c18d2206d1b034eadc532f8850c6599e904e1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-to-c-binary"></a>SQL в двоичное C:
Идентификаторы для двоичных типов данных ODBC SQL — это:  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 Следующая таблица показывает ODBC C типы данных, к которым может быть преобразован двоичных данных SQL. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Числа байт данных) \* 2 < *BufferLength*<br /><br /> (Числа байт данных) \* 2 > = *BufferLength*|data<br /><br /> Усеченные данные|Длина данных в байтах<br /><br /> Длина данных в байтах|н/д<br /><br /> 01004|  
|SQL_C_WCHAR|(Символ длина данных) \* 2 < *BufferLength*<br /><br /> (Символ длина данных) \* 2 > = *BufferLength*|data<br /><br /> Усеченные данные|Длина данных в символах<br /><br /> Длина данных в символах|н/д<br /><br /> 01004|  
|SQL_C_BINARY|Байтовая длина данных < = *BufferLength*<br /><br /> Байтовая длина данных > *BufferLength*|data<br /><br /> Усеченные данные|Длина данных в байтах<br /><br /> Длина данных в байтах|н/д<br /><br /> 01004|  
  
 При преобразовании в символьный C двоичных данных SQL каждый байт (8 бит), источник данных представляется в виде двух символов ASCII. Эти символы имеются представление символа ASCII числа в шестнадцатеричном виде. Например двоичные 00000001 преобразуется в «01» и двоичное 11111111 преобразуется в «FF».  
  
 Драйвер всегда преобразует отдельных байтов в пары шестнадцатеричных цифр и завершает символьной строки с нулевым байтом. По этой причине при *BufferLength* четное, и меньше, чем длина преобразованных данных последнего байта **TargetValuePtr* буфер не используется. (Преобразованных данных требуется четное число байтов, байт следующей последней является нулевым байтом, и не может использоваться получения последнего байта.)  
  
> [!NOTE]  
>  Разработчики приложений, не рекомендуется из привязки двоичных данных SQL в символьный тип данных C. Обычно это преобразование является неэффективной и медленной.
