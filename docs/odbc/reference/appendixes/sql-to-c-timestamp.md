---
title: 'СЗЛ в C: Меткая метка времени Документы Майкрософт'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 552bab585e4480fd922c9b9a6b112830f5c11ad9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296354"
---
# <a name="sql-to-c-timestamp"></a>Преобразование данных из SQL в C: отметки времени

Идентификатор для типа данных timestamp ODBC S'L:

- SQL_TYPE_TIMESTAMP  

В следующей таблице показаны типы данных ODBC C, в которые могут быть преобразованы данные временной метки S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  

|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > характер байт длина<br /><br /> 20 <- *<буферной длины* - длина байт-персонажа<br /><br /> *БуферНая длина* < 20|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > длина персонажа<br /><br /> 20 <- *<буферной <* - длина персонажа<br /><br /> *БуферНая длина* < 20|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Временной отметки метки времени равен нулю<br /><br /> Временной отметки метки времени является ненулевой|Данные<br /><br /> Truncated данные|6 f)<br /><br /> 6 f)|Недоступно<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Фракционная секундная часть метки времени равна нулю<br /><br /> Фракционная секундная часть метки времени незеролисл|Данные<br /><br /> Truncated данные,|6 f)<br /><br /> 6 f)|Недоступно<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|Фракционная секундная часть метки времени не усечена<br /><br /> Фракционная секундная часть метки времени усечена|Данные<br /><br /> Truncated данные|16.00<br /><br /> 16.00|Недоступно<br /><br /> 01S07|  

 Значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер*TargetValuePtr* — это размер типа данных C.  
  
 Дробные секунды метки времени усечены.  
  
 Время, временное отметка метки времени усечено.  
  
 Дата, часть метки времени игнорируется.  
  
 Дробная секундная часть метки времени усечена.  
  
 Это размер соответствующего типа данных C.  

При преобразовании данных timestamp S'L в данные символа C получена строка в "*yyyy*-*mm*-*dd* *hh:**mm*:*ss ss.** f...* формат, где до девяти цифр могут быть использованы для дробных секунд. Этот формат не зависит от настройки windows® страны. (За исключением десятичной точки и дробных секунд, весь формат должен использоваться, независимо от точности типа данных таймштампов S'L.)
